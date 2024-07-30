BANK MANAGEMENT SYSTEM SOFTWARE USING JAVA
### Complete Project Demonstration [click here](https://drive.google.com/drive/folders/1fvw2CxrDYURIYZFKtnBGsRad3snnDM9R)

### Source Code:
//Login class Source code

    package bank.management.system;
    
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    import java.sql.*;
    
    public class Login extends JFrame implements ActionListener {
        //Global declaration of button
        JButton login, reg, emp, adm;
        JPasswordField pinTextField;
        JTextField username,PinTextField;  
        Login(){
            setTitle(" BANK MANAGEMANT SYSTEM ");
            setSize(700,550);
            setLocation(350,150);        
            setLayout(null);
            ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main logo.jpg"));//Logo path setting
            Image i2 = i1.getImage().getScaledInstance(100, 100, Image.SCALE_DEFAULT);//logo placing
            ImageIcon i3= new ImageIcon(i2);
            JLabel label1 = new JLabel(i3);
            label1.setBounds(200,10,100,100);// V BANKING modifier
            add(label1);
            
        JLabel text=new JLabel("V BANKING");
        text.setFont(new Font("Osward", Font.BOLD, 38));// Font modifier
        text.setBounds(300, 40, 300, 40);
        add(text);
        
        JLabel userid=new JLabel("USER ID");
        userid.setFont(new Font("Raleway",Font.PLAIN, 18));// Font modifier
        userid.setBounds(120, 150, 400, 40);
        add(userid);
        
        username = new JTextField();
        username.setBounds(300,155,250,30);
        
        username.setFont(new Font("Arial",Font.BOLD,14));
        add(username);
        
        JLabel password=new JLabel("PASSWORD");
        password.setFont(new Font("Raleway", Font.PLAIN, 18));// Font modifier
        password.setBounds(120, 220, 400, 40);
        add(password);
        
        PinTextField = new JPasswordField();
        PinTextField.setBounds(300,225,250,30);
        
        PinTextField.setFont(new Font("Arial",Font.BOLD,14));
        add(PinTextField);
        
        login = new JButton("SIGN IN");
        login.setBounds(300,300,100,30);        
        login.addActionListener(this);
        add(login);
        // colouring the sign in button
        login.setBackground(Color.BLACK);
        login.setForeground(Color.WHITE);
        
        reg = new JButton("SIGN UP");
        reg.setBounds(300,350,100,30);
        reg.addActionListener(this);
        add(reg);
        
        emp = new JButton("EMPLOYEE");
        emp.setBounds(240,420,100,30);
        emp.addActionListener(this);
        add(emp);
        
        adm = new JButton("ADMIN");
        adm.setBounds(360,420,100,30);
        adm.addActionListener(this);
        add(adm);
        
        getContentPane().setBackground(Color.WHITE);//Changing frame background 
        setVisible(true);
    }
    
    public void actionPerformed(ActionEvent e) {
        
    if(e.getSource()== login){ 
        jdbc_connection c =new jdbc_connection();       
        String userid1 = username.getText();
        String pinnumber = PinTextField.getText();
        String query= "select * from Login where userid = '"+userid1+"' and password1 = '"+pinnumber+"'";
        try{
             ResultSet rs = c.s.executeQuery(query);
             if(rs.next()){
                 setVisible(false);
                 new transactions(pinnumber).setVisible(true);
             }else{
                 JOptionPane.showMessageDialog(null, "Incorrect User id or Pasword");
             }
             
        }catch(Exception ea){
            System.out.println(ea);
        }                    
    }else if(e.getSource()==reg){ 
        setVisible(false);
        new Customersignup().setVisible(true);         
    }else if(e.getSource()==emp){
        setVisible(false);
        new EmployeeLogin().setVisible(true);        
    }else if(e.getSource()==adm){
        setVisible(false);
        new AdminLogin().setVisible(true);
        
    }}   
    public static void main(String[] args) {
        new Login();
    }  }


//Customersignup class Source code

    package bank.management.system;

    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    public class Customersignup extends JFrame implements ActionListener {
        JTextField customer,password1,dob1,email1,acc1,userid1,pas1,pas2,address1,pincode1;
        JRadioButton male,female;
        JButton submit,back;    
        Customersignup(){
        
        JLabel emp=new JLabel("CUSTOMER DETAILS");
        emp.setBounds(250, 50, 500, 80);
        emp.setFont(new Font("Raleway",Font.BOLD,28));
        add(emp);
        
        JLabel id=new JLabel("NAME:");
        id.setBounds(150, 50, 600, 200);
        id.setFont(new Font("Raleway",Font.PLAIN,18));
        add(id);
        
        customer =new JTextField();
        customer.setBounds(360, 135, 280, 30);
        customer.setFont(new Font("Raleway",Font.PLAIN,18));
        add(customer);
        
        JLabel pass=new JLabel("FATHER'S NAME: ");
        pass.setBounds(150, 50, 600, 300);
        pass.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pass);
         
        password1=new JTextField();
        password1.setBounds(360, 185, 280, 30);
        password1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(password1);
         
        JLabel name=new JLabel("GENDER");
        name.setBounds(150, 50, 600, 400);
        name.setFont(new Font("Raleway",Font.PLAIN,18));
        add(name);
        
        male=new JRadioButton("MALE");
        male.setBounds(360, 235, 100, 30);
       add(male);
        
        female=new JRadioButton("FEMALE");
        female.setBounds(480, 235, 100, 30);
       add(female); 
        
        JLabel pos=new JLabel("DATE OF BIRTH:");
        pos.setBounds(150, 50, 600, 500);
        pos.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pos);
        
        dob1=new JTextField();
        dob1.setBounds(360, 285, 200, 30);
        dob1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(dob1);
        
        JLabel email=new JLabel("EMAIL:");
        email.setBounds(150, 50, 600, 600);
        email.setFont(new Font("Raleway",Font.PLAIN,18));
        add(email);
        
        email1=new JTextField();
        email1.setBounds(360, 335, 280, 30);
        email1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(email1);
        
        JLabel acc=new JLabel("ACCOUNT TYPE:");
        acc.setBounds(150, 50, 600, 700);
        acc.setFont(new Font("Raleway",Font.PLAIN,18));
        add(acc);
        
        acc1=new JTextField();
        acc1.setBounds(360, 385, 280, 30);
        acc1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(acc1);
        
        JLabel userid=new JLabel("USER ID:");
        userid.setBounds(150, 50, 600, 800);
        userid.setFont(new Font("Raleway",Font.PLAIN,18));
        add(userid);
        
        userid1=new JTextField();
        userid1.setBounds(360, 435, 280, 30);
        userid1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(userid1);
        
        JLabel pass1=new JLabel("PASSWORD:");
        pass1.setBounds(150, 50, 600, 900);
        pass1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pass1);
        
        pas1=new JTextField();
        pas1.setBounds(360, 485, 280, 30);
        pas1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pas1);
        
       
        JLabel pass2=new JLabel("COMFIRM PASSWORD:");
        pass2.setBounds(150, 50, 600, 1000);
        pass2.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pass2);
        
        pas2=new JTextField();
        pas2.setBounds(360, 535, 280, 30);
        pas2.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pas2);
        
        JLabel addr1=new JLabel("ADDRESS:");
        addr1.setBounds(150, 50, 600, 1100);
        addr1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(addr1);
        
        address1=new JTextField();
        address1.setBounds(360, 585, 280, 30);
        address1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(address1);
        
        JLabel pinn=new JLabel("PIN CODE:");
        pinn.setBounds(150, 50, 600, 1200);
        pinn.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pinn);
        
        pincode1=new JTextField();
        pincode1.setBounds(360, 635, 280, 30);
        pincode1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pincode1);
        
        setLayout(null);
        getContentPane().setBackground(Color.WHITE) ;
        setSize(800,800);
        setLocation(350,10);
        setVisible(true);
        
        submit=new JButton("Submit");
        submit.setBounds(250, 685, 150, 30);
        submit.addActionListener(this);
        add(submit);  
        
        
        back=new JButton("Back");
        back.setBounds(450, 685, 100, 30);
        back.addActionListener(this);
        add(back);             
    }
    public void actionPerformed(ActionEvent ae){
        String cosm1 = customer.getText(); //getText is used to get the text from textField.
        String fathername =  password1.getText();
        String dob = dob1.getText();
        String mailid = email1.getText();
        String acctype = acc1.getText();
        String userid = userid1.getText();
        String password1 = pas1.getText();
        String password2 = pas2.getText();
        String address = address1.getText();
        String pincode = pincode1.getText();
        if(ae.getSource()==back){
            setVisible(false);
            new Login().setVisible(true);
        }            
       try{
       if(cosm1.equals("")){
            JOptionPane.showMessageDialog(null, "Customer Name Is Required");
        }else if(fathername.equals("")){
            JOptionPane.showMessageDialog(null, "Father Name Is Required");
        }else if(dob.equals("")){
            JOptionPane.showMessageDialog(null, "DOB Is Required");        
        }else if(mailid.equals("")){
            JOptionPane.showMessageDialog(null, "Mail Id Required");
        }else if(acctype.equals("")){
            JOptionPane.showMessageDialog(null, "Specify Accountt Type");
        }else if(userid.equals("")){
            JOptionPane.showMessageDialog(null, "User Id Is Required");
        }else if(password1.equals("")){
            JOptionPane.showMessageDialog(null, "Password Is Required");
        }else if(password2.equals("")){
            JOptionPane.showMessageDialog(null, "Password Confirmation Required");
        }else if(address.equals("")){
            JOptionPane.showMessageDialog(null, "Address Is Required");
        }else if(pincode.equals("")){
            JOptionPane.showMessageDialog(null, "Specify Pincode");
        }else{
            jdbc_connection c =new jdbc_connection();
            String query1 = "insert into signupcustomer values('"+cosm1+"', '"+fathername+"','"+dob+"','"+mailid+"','"+acctype+"','"+userid+"','"+password1+"','"+password2+"','"+address+"','"+pincode+"')";
            String query2 = "insert into Login values('"+userid+"','"+password1+"')";

            c.s.executeUpdate(query1);           
            c.s.executeUpdate(query2); 
            JOptionPane.showMessageDialog(null, "Registered Successfully!");
            setVisible(false);
            new Login().setVisible(true);
                    }      
        } catch (Exception e){
            System.out.println(e);
        }
    }        
    public static void main(String[] args) {
        new Customersignup();        
    } 
    }



//EmployeeLogin class source code

    package bank.management.system;
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    
    
    public class EmployeeLogin extends JFrame implements ActionListener {
    
    JTextField empid1,PinTextField,name1,pos1;
    JButton log;
    
    EmployeeLogin(){       
        
        JLabel emp=new JLabel("EMPLOYEE LOGIN");
        emp.setBounds(250, 50, 500, 80);
        emp.setFont(new Font("Raleway",Font.BOLD,28));
        add(emp);
        
        JLabel id=new JLabel("EMPLOYEE ID");
        id.setBounds(150, 50, 600, 200);
        id.setFont(new Font("Raleway",Font.PLAIN,18));
        add(id);
        
        empid1=new JTextField();
        empid1.setBounds(320, 135, 280, 30);
        empid1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(empid1);
        
        JLabel pass=new JLabel("PASSWORD");
        pass.setBounds(150, 50, 600, 300);
        pass.setFont(new Font("Raleway",Font.PLAIN,18));       
        add(pass);         
             
        PinTextField = new JPasswordField();
        PinTextField.setBounds(320,185,280,30);
        
        PinTextField.setFont(new Font("Arial",Font.BOLD,14));
        add(PinTextField);
         
        JLabel name=new JLabel("EMPLOYEE NAME");
        name.setBounds(150, 50, 600, 400);
        name.setFont(new Font("Raleway",Font.PLAIN,18));
        add(name);
          
        name1=new JTextField();
        name1.setBounds(320, 235, 280, 30);
        name1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(name1);
          
          
        JLabel pos=new JLabel("POSITION");
        pos.setBounds(150, 50, 600, 500);
        pos.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pos);
        
        pos1=new JTextField();
        pos1.setBounds(320, 285, 280, 30);
        pos1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pos1);
        
        log=new JButton("LOGIN");
        log.setBounds(320, 350, 150, 30);
        //button Colouring 
        log.setBackground(Color.BLACK);
        log.setForeground(Color.WHITE);
        log.addActionListener(this);
        add(log);
        
        setLayout(null);
        getContentPane().setBackground(Color.WHITE) ;
        setSize(800,550);
        setLocation(300,150);
        setVisible(true);
        
    }
    public void actionPerformed(ActionEvent ae){
        String empid = empid1.getText(); //getText is used to get the text from textField.
        String pass =  PinTextField.getText();
        String name = name1.getText();
        String position = pos1.getText();
        
       try{
       if(empid.equals("")){
            JOptionPane.showMessageDialog(null, "Employee Id Required");
        }else if(pass.equals("")){
            JOptionPane.showMessageDialog(null, "Password Required");
        }else if(name.equals("")){
            JOptionPane.showMessageDialog(null, "Name Required");        
        }else if(position.equals("")){
            JOptionPane.showMessageDialog(null, "Name Required");
        }else{
            jdbc_connection c=new jdbc_connection();
            String query1 = "insert into signupEmp values('"+empid+"','"+pass+"','"+name+"','"+position+"')";
            String query2 = "insert into Login values('"+empid+"','"+pass+"')";
            c.s.executeUpdate(query1);            
            c.s.executeUpdate(query2);            
            
        }       
        }catch (Exception e){
            System.out.println(e);
        }
       if(ae.getSource()== log){
            setVisible(false);
            new transactions(pass).setVisible(true);
       }
    }    
    public static void main(String[] args) {
        new EmployeeLogin();
    }  
    }


//AdminLogin class Source code

    package bank.management.system;     
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    
    public class AdminLogin extends JFrame implements ActionListener {
        
    JTextField adm1,PinTextField,nam1;
    JButton log;
    AdminLogin(){
        
        JLabel emp=new JLabel("ADMIN LOGIN");
        emp.setBounds(250, 50, 500, 80);
        emp.setFont(new Font("Raleway",Font.BOLD,28));
        add(emp);
        
        JLabel id=new JLabel("ADMIN ID");
        id.setBounds(150, 50, 600, 200);
        id.setFont(new Font("Raleway",Font.PLAIN,18));
        add(id);
        
        adm1=new JTextField();
        adm1.setBounds(320, 135, 280, 30);
        adm1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(adm1);
        
        JLabel pass=new JLabel("PASSWORD");
        pass.setBounds(150, 50, 600, 300);
        pass.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pass);
  
        PinTextField = new JPasswordField();
        PinTextField.setBounds(320,185,280,30);
        
        PinTextField.setFont(new Font("Arial",Font.BOLD,14));
        add(PinTextField);
         
      
        JLabel pos=new JLabel("NAME");
        pos.setBounds(150, 50, 600, 400);
        pos.setFont(new Font("Raleway",Font.PLAIN,18));
        add(pos);
        
        nam1=new JTextField();
        nam1.setBounds(320, 235, 280, 30);
        nam1.setFont(new Font("Raleway",Font.PLAIN,18));
        add(nam1);
        
        log=new JButton("LOGIN");
        log.setBounds(320, 280, 150, 30);
        //button Colouring 
        log.setBackground(Color.BLACK);
        log.setForeground(Color.WHITE);
        log.addActionListener(this);
        add(log);
                
        setLayout(null);
        getContentPane().setBackground(Color.WHITE) ;
        setSize(800,550);
        setLocation(300,150);
        setVisible(true);
        
    }
    public void actionPerformed(ActionEvent ae){
        String admid = adm1.getText(); //getText is used to get the text from textField.
        String pass =  PinTextField.getText();
        String name = nam1.getText();
        if(ae.getSource()==log){
            setVisible(false);
            new admin_interface().setVisible(true);
        }        
        
    try{
        if(admid.equals("")){
            JOptionPane.showMessageDialog(null, "Admin Id Required");
        }else if(pass.equals("")){
            JOptionPane.showMessageDialog(null, "Password Required");
        }else if(name.equals("")){
            JOptionPane.showMessageDialog(null, "Name Required");
        }else{
            jdbc_connection c=new jdbc_connection();
            String query1 = "insert into signupAdm values('"+admid+"','"+pass+"','"+name+"')";           
            c.s.executeUpdate(query1);             
            }        
        }catch (Exception e){
        System.out.println(e);
        }
    }    
    public static void main(String[] args) {
        new AdminLogin();
    }    
    }



//transactions class Source code

    package bank.management.system;
    
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    
    public class transactions extends JFrame implements ActionListener {
    
    JButton deposit,withdraw,pinchange,balance,exit; 
    String pinnumber;
    transactions(String pinnumber){ 
        this.pinnumber = pinnumber;
        
        setLayout(null);      

        ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main_tbg.jpg"));//Logo path setting
        Image i2 = i1.getImage().getScaledInstance(900, 900, Image.SCALE_DEFAULT);//logo placing
        ImageIcon i3= new ImageIcon(i2);
        JLabel image = new JLabel(i3);
        image.setBounds(0,0,900,900);
        add(image);
        
        JLabel text1 =new JLabel("Welcome To V Online BANKING ");
        text1.setBounds(222,80,700,35);
        text1.setForeground(Color.WHITE);
        text1.setFont(new Font("System", Font.BOLD, 30));
        image.add(text1);
        
        JLabel text2 =new JLabel("Please Select Your Transaction");
        text2.setBounds(250,150,700,35);
        text2.setForeground(Color.WHITE);
        text2.setFont(new Font("System", Font.BOLD, 25));
        image.add(text2);
        
        deposit =new JButton("Deposit");
        deposit.setBounds(160, 250, 200, 50);
        deposit.addActionListener(this);
        image.add(deposit);

        withdraw =new JButton("Withdraw");
        withdraw.setBounds(160, 350, 200, 50);
        withdraw.addActionListener(this);
        image.add(withdraw);
        
        pinchange =new JButton("Pin Change");
        pinchange.setBounds(520, 250, 200, 50);
        pinchange.addActionListener(this);
        image.add(pinchange);
        
        balance =new JButton("Balance Enquiry");
        balance.setBounds(520, 350, 200, 50);
        balance.addActionListener(this);
        image.add(balance);
        
        exit =new JButton("Exit");
        exit.setBounds(360, 450, 160, 50);
        exit.addActionListener(this);
        image.add(exit);
 
        setTitle(" BANK MANAGEMANT SYSTEM ");
        setSize(900,900);
        setLocation(230,0);
        setUndecorated(true);
        setVisible(true);         
        
    } 
        
    public void actionPerformed(ActionEvent ae){         
        if (ae.getSource()== exit ){
            System.exit(0);
        }else if(ae.getSource()== deposit){
            setVisible(false);
            new deposit(pinnumber).setVisible(true);
        }else if(ae.getSource()== withdraw){
            setVisible(false);
            new withdrawal(pinnumber).setVisible(true);
        }
        else if(ae.getSource()== balance){
            setVisible(false);
            new balance(pinnumber).setVisible(true);
        }
        
    }   
    
    public static void main(String[] args) {
        new transactions("");
    }   
    }



//deposit class Source code

    package bank.management.system;
    
    import java.awt.*;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    import javax.swing.*;
    import java.util.*;
    
    public class deposit extends JFrame implements ActionListener{
    
    JTextField amount;
    JButton deposit,backb;
    String pinnumber;
    
    deposit(String pinnumber){
        this.pinnumber = pinnumber;
        
        setLayout(null);
        
        ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main_tbg.jpg"));//Logo path setting
        Image i2 = i1.getImage().getScaledInstance(900, 900, Image.SCALE_DEFAULT);//logo placing
        ImageIcon i3= new ImageIcon(i2);
        JLabel image = new JLabel(i3);
        image.setBounds(0,0,900,900);
        add(image);
        
        
        JLabel text=new JLabel("Enter The Amount To Be Deposited");
        text.setForeground(Color.WHITE);
        text.setFont(new Font("System",Font.BOLD,30));
        text.setBounds(200,80,700,35);        
        image.add(text);
        
        amount = new JTextField();
        amount.setBounds(300,200,300,50);        
        amount.setFont(new Font("Raleway",Font.BOLD,30));
        image.add(amount);
        
        
        deposit =new JButton("Deposit");
        deposit.setBounds(350, 300, 200, 50);
        deposit.addActionListener(this);
        image.add(deposit);
        
        backb =new JButton("Back");
        backb.setBounds(350, 400, 200, 50);
        backb.addActionListener(this);
        image.add(backb);     
           
        
        setTitle(" BANK MANAGEMANT SYSTEM ");
        setSize(900,900);
        setLocation(230,0);
        //setUndecorated(true);
        setVisible(true); 
        
    }
    
    public void actionPerformed(ActionEvent ae){    
        try{
       if(ae.getSource()==deposit )
       {
           String amountvalue=amount.getText();
           Date date=new Date();
           if(amountvalue.equals(""))
           {
               JOptionPane.showMessageDialog(null,"Please Enter The Valid Amount!");
           }else
           {
               jdbc_connection c=new jdbc_connection();
                String query2 = "insert into bank values('"+pinnumber+"','"+date+"','Deposit','"+amountvalue+"')";            
                c.s.executeUpdate(query2);
                JOptionPane.showMessageDialog(null,"Rs "+amountvalue+" Depositted Successfully");
                setVisible(false);
                new transactions(pinnumber).setVisible(true);
           }
           
       }else if(ae.getSource()==backb){
           setVisible(false);
           new transactions(pinnumber).setVisible(true);
           
        }
            
            
       }catch(Exception e){
               System.out.println(e);
               }
        
    }   
    
    public static void main(String[] args) {
        new deposit("");
        
    } 
    }



//withdrawal class Source code

    package bank.management.system;
    
    import java.awt.*;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    import javax.swing.*;
    import java.util.*;
    
    public class withdrawal extends JFrame implements ActionListener {

    JTextField amount;
    JButton withdraw, backb;
    String pinnumber;

    withdrawal(String pinnumber) {
        this.pinnumber = pinnumber;

        setLayout(null);

        ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main_tbg.jpg"));//Logo path setting
        Image i2 = i1.getImage().getScaledInstance(900, 900, Image.SCALE_DEFAULT);//logo placing
        ImageIcon i3 = new ImageIcon(i2);
        JLabel image = new JLabel(i3);
        image.setBounds(0, 0, 900, 900);
        add(image);

        JLabel text = new JLabel("Enter The Amount To Be Waithdrawn");
        text.setForeground(Color.WHITE);
        text.setFont(new Font("System", Font.BOLD, 30));
        text.setBounds(200, 80, 700, 35);
        image.add(text);

        amount = new JTextField();
        amount.setBounds(300, 200, 300, 50);
        amount.setFont(new Font("Raleway", Font.BOLD, 30));
        image.add(amount);

        withdraw = new JButton("Withdraw");
        withdraw.setBounds(350, 300, 200, 50);
        withdraw.addActionListener(this);
        image.add(withdraw);

        backb = new JButton("Back");
        backb.setBounds(350, 400, 200, 50);
        backb.addActionListener(this);
        image.add(backb);

        setTitle(" BANK MANAGEMANT SYSTEM ");
        setSize(900, 900);
        setLocation(230, 0);
        //setUndecorated(true);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent ae) {
        try {
            if (ae.getSource() == withdraw) {
                String amountvalue = amount.getText();
                Date date = new Date();

                if (amountvalue.equals("")) {
                    JOptionPane.showMessageDialog(null, "Please Enter The Valid Amount <= 10,000");
                } else if (Integer.parseInt(amountvalue) <= getBalance()) {
                    JOptionPane.showMessageDialog(null, "Insufficient Balance or Invalid Amount");
                } else {
                    jdbc_connection c = new jdbc_connection();
                    String query2 = "insert into bank values('" + pinnumber + "','" + date + "','Waithdraw','" + amountvalue + "')";
                    c.s.executeUpdate(query2);
                    JOptionPane.showMessageDialog(null, "Rs " + amountvalue + "/- Waithdrawn Successfully");
                    setVisible(false);
                    new transactions(pinnumber).setVisible(true);
                }

            } else if (ae.getSource() == backb) {
                setVisible(false);
                new transactions(pinnumber).setVisible(true);
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }

    public static void main(String[] args) {
        new withdrawal("");
    }

    private int getBalance() {
        // Implement code to retrieve the current balance from the database
        // using the provided PIN number
        int balance = 0; // Replace with actual balance retrieval logic
        return balance;
    }
    }




//balance class Source code

    package bank.management.system;    
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    import java.util.*;
    import java.sql.*;
    
    public class balance extends JFrame implements ActionListener{
    
    JButton backb;
    String pinnumber;
    
    balance(String pinnumber){
        this.pinnumber = pinnumber;
        
        setLayout(null);   
        ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main_tbg.jpg"));//Logo path setting
        Image i2 = i1.getImage().getScaledInstance(900, 900, Image.SCALE_DEFAULT);//logo placing
        ImageIcon i3= new ImageIcon(i2);
        JLabel image = new JLabel(i3);
        image.setBounds(0,0,900,900);
        add(image);        
        
        jdbc_connection c=new jdbc_connection();
        int balance=0;
        try{
            ResultSet rs=c.s.executeQuery("select * from bank where pin ='"+pinnumber+"'");           

            while (rs.next()){
                if(rs.getString("type").equals("Deposit")){
                    balance += Integer.parseInt(rs.getString("amount"));
                }else{
                    if(balance < 0){
                        System.out.println("Insufficient Balance");
                        
                        break;
                    }else{
                        balance -= Integer.parseInt(rs.getString("amount"));
                       }
                       }               
            }             
            }catch(Exception e){
            System.out.println(e);
        }
        JLabel text=new JLabel("Your Current Account Balance is Rs "+balance+"/-");
        text.setForeground(Color.WHITE);
        text.setFont(new Font("System",Font.BOLD,30));
        text.setBounds(150,250,700,35);        
        image.add(text);
                      
        backb =new JButton("Back");
        backb.setBounds(350, 400, 200, 50);
        backb.addActionListener(this);
        image.add(backb);     
           
        
        setTitle(" BANK MANAGEMANT SYSTEM ");
        setSize(900,900);
        setLocation(230,0);
        //setUndecorated(true);
        setVisible(true); 
        
    }
    
    @Override
    public void actionPerformed(ActionEvent ae) {
        if(ae.getSource()==backb){
            setVisible(false);
            new transactions(pinnumber).setVisible(true);
        }        
    }   
    public static void main(String[] args) {
        new balance("");
         }    
    }



//balance class Source code
    package bank.management.system;
    
    import java.awt.*;
    import java.awt.event.*;
    import javax.swing.*;
    import java.util.*;
    import java.sql.*;
    
    public class balance extends JFrame implements ActionListener{
    
    JButton backb;
    String pinnumber;
    
    balance(String pinnumber){
        this.pinnumber = pinnumber;
        
        setLayout(null);
   
        ImageIcon i1 = new ImageIcon(ClassLoader.getSystemResource("icons/main_tbg.jpg"));//Logo path setting
        Image i2 = i1.getImage().getScaledInstance(900, 900, Image.SCALE_DEFAULT);//logo placing
        ImageIcon i3= new ImageIcon(i2);
        JLabel image = new JLabel(i3);
        image.setBounds(0,0,900,900);
        add(image);        
        
        jdbc_connection c=new jdbc_connection();
        int balance=0;
        try{
            ResultSet rs=c.s.executeQuery("select * from bank where pin ='"+pinnumber+"'");
            

            while (rs.next()){
                if(rs.getString("type").equals("Deposit")){
                    balance += Integer.parseInt(rs.getString("amount"));
                }else{
                    if(balance < 0){
                        System.out.println("Insufficient Balance");
                        
                        break;
                    }else{
                        balance -= Integer.parseInt(rs.getString("amount"));                        
                    }
                }               
            }            
            
        }catch(Exception e){
            System.out.println(e);
        }
        JLabel text=new JLabel("Your Current Account Balance is Rs "+balance+"/-");
        text.setForeground(Color.WHITE);
        text.setFont(new Font("System",Font.BOLD,30));
        text.setBounds(150,250,700,35);        
        image.add(text);
                      
        backb =new JButton("Back");
        backb.setBounds(350, 400, 200, 50);
        backb.addActionListener(this);
        image.add(backb);               
        
        setTitle(" BANK MANAGEMANT SYSTEM ");
        setSize(900,900);
        setLocation(230,0);
        //setUndecorated(true);
        setVisible(true); 
        
    }    
    @Override
    public void actionPerformed(ActionEvent ae) {
        if(ae.getSource()==backb){
            setVisible(false);
            new transactions(pinnumber).setVisible(true);
        }        
    }    
    public static void main(String[] args) {
        new balance("");
      }      
    } 


//admin_interface class Source code

    package  bank.management.system;
    import java.awt.Color;
    import java.awt.Font;
    import javax.swing.*;
    import java.sql.*;
    
    public class admin_interface extends JFrame {

    admin_interface(){
        
        setTitle("Database");
        
        setLayout(null);
        
        JLabel mini1 = new JLabel();
        add(mini1);
        
        JLabel mini2 = new JLabel();
        add(mini2);
        
        JLabel bank = new JLabel("V Bank");
        bank.setBounds(250,80,100,20);
        bank.setFont(new Font("Raleway",Font.BOLD,28));
        add(bank);
        
        JLabel userlab = new JLabel("Customer Id        |       Customer Name");
        userlab.setBounds(50,200,300,20);
        add(userlab);
        
        JLabel userlab_line = new JLabel("______________________________");
        userlab_line.setBounds(50,205,250,20);
        add(userlab_line);
        
        JLabel emp1 = new JLabel("Employee Id       |       Employee Name       |       Position");
        emp1.setBounds(300,200,300,20);
        add(emp1);
        
        JLabel emp_line = new JLabel("__________________________________________");
        emp_line.setBounds(300,205,300,20);
        add(emp_line);
        
        JLabel card=new JLabel();
        card.setBounds(280,150,300,60);
        add(card);  
        
        //Customer details retrival
        
        try{
        jdbc_connection c=new jdbc_connection();
        ResultSet rs= c.s.executeQuery("select * from signupcustomer");
        while(rs.next()){
            mini1.setText(mini1.getText()+"<html>"+rs.getString("userid")+"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"+ rs.getString("cosm1")+"<br><br><html>");
        }
            
            
        }catch(Exception e){
            System.out.println(e);
        }
        
        mini1.setBounds(50,10,400,500);
        
        //Employee details retrival        
        
        try{
        jdbc_connection c=new jdbc_connection();
        ResultSet rs= c.s.executeQuery("select * from signupEmp");
        while(rs.next()){
            mini2.setText(mini2.getText()+"<html>"+rs.getString("empid")+"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"+ rs.getString("name")+"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"+ rs.getString("position")+"<br><br><html>");
        }
            
            
        }catch(Exception e){
            System.out.println(e);
        }
        
        mini2.setBounds(300,10,400,500);
        
        setSize(680,750);
        setLocation(450,0);
        getContentPane().setBackground(Color.WHITE);
        setVisible(true);
        
    }
    public static void main(String[] args) {
        new admin_interface();
    }
    }


//jdbc_connection class Source code

    package bank.management.system;
    
    import java.sql.*;
    
    public class jdbc_connection {
        Connection c;    
    
    //creating Statement
    Statement s;

    public jdbc_connection(){
        try{//NO need of Registering to the driver because the imported library(mysql-connector-java) done that task.
            //creating connection
            c = DriverManager.getConnection("jdbc:mysql:///bankmanagementsystem","root","ramupalla912@2002");
            s= c.createStatement();
        
        } catch(Exception en){
            System.out.println(en);
        }
    }
    }

