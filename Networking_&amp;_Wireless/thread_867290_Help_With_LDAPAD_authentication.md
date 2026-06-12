---
title: "Help With LDAP/AD authentication"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by arstacey on 2008-07-22
I am trying to get some code to authenticate users in our Active Directory domain on my Ubuntu server using the php ldap function.  I keep getting the error:

Warning: ldap_bind() [function.ldap-bind]: Unable to bind to server: Invalid credentials in /var/www/auth.php on line 31
Could not bind to cn=andrew,

Line 31 is the one below that says:

if (!($bind = ldap_bind($connect, "$dn" . "$basedn",$password))) {

Can somebody tell me what I am doing wrong?  I am VERY new to this so go easy, lol.

[PHP]
<?php
$server="OUR AD SERVER";        
$basedn="ou=employees, dc=OurDomain, dc=OurDomain";        
$script=$_SERVER['SCRIPT_NAME'];
if (isset($HTTP_COOKIE_VARS['cookie'])) {         //If cookie exists, retrieve it and put it in an array for use.
        $cookie=$HTTP_COOKIE_VARS['cookie'];
        }
if (isset($cookie)) {                                 
        $username=$cookie['user'];
        $password=($cookie['token']);
        $fullname=$cookie['fullname'];
        $fqdn=$cookie['fqdn'];
        $dn = "cn=$username, ";
                if (!($connect = ldap_connect($server))) {
                        die ("Could not connect to LDAP server");
                }

                if (!($bind = ldap_bind($connect, "$dn" . "$basedn", $password))) {
                        die ("Could not bind to $dn$basedn");
                }
        } else {
                if ((isset($_POST['username'])) && (isset($_POST['password']))) {
                        $username=$_POST['username'];
                        $password=$_POST['password'];
                        $filter="(&(|(!(displayname=Administrator*))(!(displayname=Admin*)))(cn=$username))";        //define an appropriate ldap search filter to find your users, and filter out accounts such as administrator(administrator should be renamed anyway!).
                        $dn = "cn=$username, ";
                                if (!($connect = ldap_connect($server))) {
                                        die ("Could not connect to LDAP server");
                                }

                                if (!($bind = ldap_bind($connect, "$dn" . "$basedn",$password))) {
                                        die ("Could not bind to $dn");
                                }
                $sr = ldap_search($connect, $basedn,"$filter");
                $info = ldap_get_entries($connect, $sr);
                $fullname=$info[0]["displayname"][0];
                $fqdn=$info[0]["dn"];
                setcookie("cookie[user]",$username);
                setcookie("cookie[token]",$password);
                setcookie("cookie[fullname]",$fullname);
                setcookie("cookie[fqdn]", $fqdn);
        } else {
?>


<html>
<head>
<title>Portal Login</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<meta http-equiv="expires" content="0">
<meta http-equiv="pragma" content="no-cache">
</head>
<SCRIPT LANGUAGE="JavaScript">
        <!--
                document.onmousedown=click;
                function click()
                {
                        if (event.button==2) {alert('Right-clicking has been disabled by the administrator.');}
                }
                
        //-->
        </SCRIPT>
<div align="center">
<form method="post" action="<? echo $script; ?>">
<div align="center">

<table width="210" border="0" cellspacing="0" cellpadding="0">
<tr>
<td align="center">
<fieldset>
<Legend><font face="Verdana,Tahoma,Arial,sans-serif" size="1"
color="gray">Enter Credentials</font></Legend>
<table border="0" cellspacing="3" cellpadding="0">
<tr>
<td align="right" valign="middle"><b><font
face="Verdana,Tahoma,Arial,sans-
serif" size="1" color="gray">Username:</font></td>
<td align="center" valign="middle">
<input class="clear" type="text" size="15" name="username">
</td>
</tr>
<tr>
<td align="right" valign="middle"><b><font
face="Verdana,Tahoma,Arial,sans-
serif" size="1" color="gray">Password:</font></td>
<td align="center" valign="middle">
<input class="pass" type="password" size="15"
name="password">
</td>
</tr>
</table>
<input type=image src="images/login.gif" alt="Login"
name="image">
<br>
</div>
</td>
</tr>
         </fieldset>
</table>
<br>
<table width="640"><tr><td align="center">
<font face="Verdana,Tahoma,Arial,sans-serif" size="1"
color="silver">This System is
for the use of authorized users only. Individuals using this computer system
without
authority, or in excess of their authority, are subject to having their activities
on this system
monitored and recorded by system personnel. In the course of monitoring individuals
improperly using this system, or in the course of system maintenance, the activities
of
authorized users may also be monitored. Anyone using this system expressly consents
to
such monitoring and is advised that if such monitoring reveals possible criminal
activity,
system personnel may provide the evidence of such monitoring to law enforcement
officals.
This warning has been provided by the United States Department of Justice and is
intended to
ensure that monitoring of user activity is not in violation of the Communications
Privacy Act of
1986.</font>
</td></tr></table>

</div>
</form>

</div>
</body>
</html>
<?
die ();
}
}
?>
[/PHP]

---

