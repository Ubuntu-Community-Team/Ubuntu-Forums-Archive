---
title: "Login to Authentication (Open) network using commandline."
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by john303 on 2014-10-06
In my company have a wifi network, for example 'WNETWORK', after connect, I must enter my account, includes ID and password for each one.
So I have three information, include: name of network, name of ID, and password to establish a connection.
How to connect to this network which only using commandline. Please give me the way to config.
Thank you so much!

---

### Post by ian-weisser on 2014-10-06
> **john303 said:**
> after connect, I must enter my account, includes ID and password for each one.

What are you entering them into? A web browser page? An application?

---

### Post by john303 on 2014-10-06
A webrowser. Thanks

---

### Post by ian-weisser on 2014-10-06
You must look at the html source of the web page.

If the input uses javascript, then I see no way around using the web page - the browser needs to load and run the javascript.
If the input uses an ordinary html POST, then you can push login data using curl...or perhaps even wget.

Either way, it's not trival - and was made deliberately non-trivial (sometimes to prevent exactly the kind of automated login that you are trying to do) by whomever set up the network and web page.

So, being a good network citizen, your first stop should be the network owner...to ask permission for automated or script login to their network. They can probably enable it quite easily.

---

### Post by john303 on 2014-10-07
Here is script code, please give me a solution. Thank so much!!
```
<!--------------------------------------------------------------------------------------------------------->

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>XXXXX Public Hotspot</title>
<style type="text/css">
body {
 background-color: #FFF;
}
.offer {
 font-size: 24px;
 color: #F00;
 text-align: center;
}
.bolder {
 border: 1px solid #FFF;
}
.copyright {
 font-size: 12px;
 text-align: center;
 color: #FFF;
}
.button {
 font-size: 16px;
 font-weight: bold;
}
body,td,th {
 color: #000;
 font-family: Arial, Helvetica, sans-serif;
 font-size: 16px;
}
</style>
</head>

 <title>Anonymous Login</title>
<body>
  <form method="post" action="http://xxxxxx:8002/">
  <input name="redirurl" type="hidden" value="http://www.xxxxxx">
    <center>
   <table cellpadding="6" cellspacing="0" width="780" height="380" style="border:1px solid #000000">
     <tr height="10" bgcolor="#000099">
      <td align="center" style="border-bottom:1px solid #000000">      
       <font color='white'>
        <b><h3>
         Welcome to XXX  Public Hotspot
        </h3></b></font></td>
     </tr>
     <tr>
      <td>
       <div id="mainlevel">
        <center>
         <table width="100%" border="0" cellpadding="5" cellspacing="0">
          <tr>
           <td>
            <center>
             <div id="mainarea">
              <center>
               <table width="100%" border="0" cellpadding="5" cellspacing="5">
                <tr>
                 <td>
                  <div id="maindivarea">
                   <center>
                    <div id='statusbox'>
                     <font color='red' face='arial' size='+2'>
                      <b>
                     
                      </b>
                     </font>
                     <font color='blue' face='arial' size='+1'>
                     WARNING: You should XXX Wifi Network if you have XXX account<br><br>
                     You will be limited access to something if you use the Wifi Network<br><br>
                     </font>
                     If you have any difficulties you may contact us at XXXX<br></div>
                    <br/>
                    <div id='loginbox'>
                     <table>
                        <tr><td align="right">Username:</td><td><input name="auth_user" type="text" value="anonymous" readonly></td></tr>
                        <tr><td align="right">Password:</td><td><input name="auth_pass" type="password" value="dhbk" readonly></td></tr>
                        <tr>
                          <td colspan="2" align="right">&nbsp;</td>
                        </tr>          
                        <td align="right">&nbsp;</td>
                        <td><input name="accept" type="submit" class="button" value="Continue"></td>
                        </tr>
                        <tr>
                        <td align="right"></td><td></td></tr>
                     </table><br />
                    </div>
                   </center>
                  </div>
                 </td>
                </tr>
               </table>
              </center>
             </div>
            </center>
           </td>
          </tr>
         </table>
        </center>
       </div>
      </td>
     </tr>
     <tr height="10" bgcolor="#000099">
      <td align="center" style="border-bottom:1px solid #000000">
        <font color='white'>
          <b>
        </b></font></td>
     </tr>
     </table>
   </center>
</form>
</body>
</html>
```

---

