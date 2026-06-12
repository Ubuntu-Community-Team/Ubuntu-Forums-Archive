---
title: "Problem reading mysql table with php"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by vinaykumarjg on 2011-06-15
Hi all,

   I have installed mysql, apache2 and php5. they work fine. But when I try to read a table with php it shows me the blank page. Have i left any thing? I need to know. Here's the code I've used.

 [PHP]
<?
$c = mysql_connect("localhost","vinay","vinay");
mysql_select_db("myweb",$c);

$res = mysql_query("select * from member_info",$c);
$data = mysql_fetch_array($res);
print "<pre>";
print_r ($data);
print "</pre>";
?>
[/PHP]Please reply me asap.

Thank you.

---

### Post by Lazaruss on 2011-06-15
I'd guess you're getting a blank page because error reporting is off. is it not mysql_fetch_assoc or mysql_fetch_array?

put the following after the <?php tag
```
error_reporting(E_ALL);
```

don't forget to remove it in production

---

### Post by dozycat on 2011-06-15
try this:


```

	$conn = new mysqli('domain', $user, $pwd, 'database') or die ('Cannot open database');
	
	
	
	$sql = "SELECT * FROM table";
	$result = $conn->query($sql) or die(mysqli_error());
        while ($row = $result->fetch_assoc()){
                 // do something with the current record
         }




```

---

### Post by vinaykumarjg on 2011-06-15
Thanks for the reply. But both of the ways still  leaves me blank page. Is there any wrong with the configuration?

---

### Post by dozycat on 2011-06-15
follow this:

[HTML]http://www.willfitch.com/mysqli-tutorial.html[/HTML]

first case you must call the variables according to your sql string.

Second case the problem could be  with your domain string, put an echo after the die. That way you can see if the code is going after die.

---

### Post by Maheriano on 2011-06-15
```
$sql = mysql_query("select * from member_info");
$sqlRow = mysql_fetch_assoc($sql);
echo "value: " . $sqlRow['column'];

```

Replace column with the name of the column you want to get the value from.

If that doesn't work, you did something wrong.

---

### Post by vinaykumarjg on 2011-06-15
thanks a lot. It solved my problem. But I have a question. I need to  why did the previous code didn't work?
Is there any other ways to solve the problem.


 Thanks again.



   vinay

---

### Post by vinaykumarjg on 2011-06-15
> **dozycat said:**
> follow this:

[HTML]http://www.willfitch.com/mysqli-tutorial.html[/HTML]first case you must call the variables according to your sql string.

Second case the problem could be  with your domain string, put an echo after the die. That way you can see if the code is going after die.


[PHP]Thats a great tutorial. Thanks dozycat.[/PHP]

---

### Post by dozycat on 2011-06-15
maybe mysql_fetch_assoc instead of mysql_fetch_a?

---

### Post by Maheriano on 2011-06-15
> **dozycat said:**
> maybe mysql_fetch_assoc instead of mysql_fetch_a?

Yes, you were missing 4 letters from this line.

---

