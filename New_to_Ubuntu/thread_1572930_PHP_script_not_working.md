---
title: "PHP script not working"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2010-09-11
I have picked the following script from a book on php programming with mysql.
I am using Lucid, Apache2 server ver 2.2.14-5, mysql 5.1.41-3 & php5.
The scripts are as follows:

#dbconnect.php - filename
[HTML]<?php
$dbUser = 'my_name';
$dbPass = 'my_pass';
$dbName = 'guestbook';
$dbHost = 'localhost';


$sql = mysql_connect($dbHost, $dbUser, $dbPass)
		or die (mysql_error());
mysql_select_db($dbName, $sql) or die (mysql_error());
?>
[/HTML]
# sign.php - filename
[HTML]<h2>Sign my Guest Book !!!</h2>

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

<input type=submit name=submit value="Sign">
<input type=reset name=reset value="Start Over">

</form>
[/HTML]
#create_entry.php - filename
[HTML]<?php
include('dbconnect.php');

if($submit == "Sign")
{
	$query = "insert into guestbook
		(name, location, email, url, comments) values
		('$name', '$location', '$email', '$url', '$comments')";
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
[/HTML]

#view.php - filename
[HTML]<?php
include('dbconnect.php');
?>
<h2>View My Guest Book!!!</h2>

<?php

$result = mysql_query("select * from guestbook") or
	die (mysql_error());
while ($row = mysql_fetch_array($result))
{
	echo "<b>Name:</b>";
echo $row["name"];
echo "<br>\n";
echo "<b>Location:</b>";
echo $row["location"];
echo "<br>\n";
echo "<b>Email:</b>";
echo $row["email"];
echo "<br>\n";
echo "<b>URL:</b>";
echo $row["url"];
echo "<br>\n";
echo "<b>Comments:</b>";
echo $row["comments"];
echo "<br>\n";
echo "<br>\n";
echo "<br>\n";
}
mysql_free_result($result);
?>

<h2><a href="sign.php">Sign My Guest Book !!!</a></h2>
[/HTML]

All the above files are in single dir.
The above scripts do not give the desired results as shown in the book.
I have created a db named guestbook containing one table named guestbook.
I have run another php script with mysql and it worked just fine.
Is there a problem with the code?
or have the commands changed with new ver of php?
The working script also uses the same username and password. Could that be the problem?
Any help will be highly appreciated. Thanks in advance.:)

---

### Post by mowglinz on 2010-09-12
Cook Steel is correct. You need to have the scripts within the DocumentRoot of a configured apache host. If you have that then what exactly are the undesirable results? Is anything being logged to /var/log/mysql.log or  /var/log/apache2/error.log.

---

### Post by gupta_sumesh63 on 2010-09-12
Thanks for the reply. I checked the error logs. It says 
"undefined variable $submit in file create_entry.php."
I thought all elements of a form can be passed as variables to the php script. 
What am I missing here?
Thanks in advance:(

---

### Post by garyed on 2010-09-12
I don't think $submit is a variable because it wasn't defined before you used it in the if statement. I'm not much of a programmer but you probably would be better off just using create_entry.php to check that the form in sign.php was filled out correctly. Something like this:

```


 if ($_POST['name']=="")
 { $notify = "No name entered<br/>";}
 if ($_POST['location']=="")
 { $notify .= "No location entered<br/>";}
 if ($_POST['email']=="")
 { $notify .= " No email address entered<br/>";}
 if ($_POST['name']=="" || $_POST['location']=="" || $_POST['email']=="")
 { die ("$notify click the back button and try again");}


```

Then you could follow that with your query.

Good luck

---

### Post by v1ad on 2010-09-12
yea you need to transfer the variable from one document to the other.

---

### Post by TCHebb on 2010-09-12
Instead of just $<fieldname>, you need to use $_POST['<fieldname>'] in the PHP script.

---

### Post by v1ad on 2010-09-12
$submit = $_POST['submit']; where you are checking the submit value,

and in the other document 
<form action="create_entry.php" method="post">

o since you already have the form action just do $submit = $_POST['submit']; in the create_entry.php form.

---

### Post by gupta_sumesh63 on 2010-09-13
Thanks a lot all of you. That was a speedy solution and it worked. Very appreciable. I have just started learning  php scripting and the book is written with lot of syntax errors and missing lines.
Thanks again.
PS how do I mark this as solved?

---

### Post by v1ad on 2010-09-13
on the top, thread tools, click it and then solved.

---

