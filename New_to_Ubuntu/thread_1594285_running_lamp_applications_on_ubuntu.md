---
title: "running lamp applications on ubuntu"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by tbaba83 on 2010-10-12
hello am new here. i have a difficult problem i have been trying to solve for the past few months. i just installed lamp on ubuntu 10.08 and started building my first database application.  i intend to build a form. the form is called sign.php and the script is defined below.

<h2>Sign my Guest Book!!!</h2>
<form method=post action="create_entry.php">
<b>Name:</b>
<input type=text size=40 name=name>
<br>
<b>Location:</b>
<input type=text size=40 name=location>
<br>
<b>Email:</b>
<input type=text size=40 name=email>
<br>
<b>Home Page URL:</b>
<input type=text size=40 name=url>
<br>
<b>Comments:</b>
<textarea name=comments cols=40 rows=4 wrap=virtual></textarea>
<br>
<input type=submit name=submit value="Sign!">
<input type=reset name=reset value="Start Over">
</form>

now the action of the sign.php form is the create_entry.php script whose script is found below:

<?php
include("dbconnect.php");
if ($submit == "Sign!")
{
     $query = "insert into guestbook
         (name,location,email,url,comments) values
         ('$name', '$location', '$email', '$url', '$comments')"
     ;
     mysql_query($query) or
              die (mysql_error());
?>
<h2>Thanks!!</h2>
<h2><a href="view.php">View My Guest Book!!!</a></h2>
<?php
}
else
{
     include("sign.php");
}
?>

found within the create_entry.php script is the dbconnect.php whose script is found below;

mysql_connect("localhost", "root","mobolaji") or
    die ("Could not connect to database");
mysql_select_db("guestbook") or
    die ("Could not select database");


now i have created the database guestbook and also a table called guestbook within this database in mysql but everytime i run the sign.php form and i input entries into the form, i get this;

mysql_connect("localhost", "root","mobolaji") or die ("Could not connect to database"); mysql_select_db("guestbook") or die ("Could not select database");

i have experienced this same problem in windows and i was told to go into the config.inc.php file and edit the username and password. that worked in windows but in ubuntu it didnt. i need help seriously. thanks

---

### Post by ieee488 on 2010-10-12
Before you start using your PHP forms, you need to verify your MySQL installation.

Follow the directions [here]("http://www.devshed.com/c/a/MySQL/MySQL-Configuration-and-Installation/6/") by logging in using the username and password you are using in your form.

---

