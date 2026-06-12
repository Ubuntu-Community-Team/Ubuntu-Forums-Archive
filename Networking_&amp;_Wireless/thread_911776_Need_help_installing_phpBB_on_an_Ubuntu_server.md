---
title: "Need help installing phpBB on an Ubuntu server"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by jamieh on 2008-09-06
I downloaded phpBB3 and I put the files into a folder on my Ubuntu server with Apache which is sucessfully holding websites this second.

I read the [documentation]("http://www.phpbb.com/support/documentation/3.0/quickstart/quick_installation.php") for it, and it said to point my web browser to that folder and it will start an installer, but instead it just wants me to download some .phtml file. Firefox on the server, Firefox on the Fedora machine, and Safari on the MacBook all do this. What did I do wrong?

Thanks

---

### Post by cdtech on 2008-09-06
What PHP version are you using? Here is a small script to test the PHP install.
```
<html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html>
```
Save as "info.php" and point your browser to it. If it doesn't display I would check your install.

Hope this helps ya.....

---

### Post by jamieh on 2008-09-09
> **cdtech said:**
> What PHP version are you using? Here is a small script to test the PHP install.
```
<html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html>
```
Save as "info.php" and point your browser to it. If it doesn't display I would check your install.

Hope this helps ya.....

Still won't work :(

It just tries to download the file to my computer

---

### Post by cdtech on 2008-09-09
Do you have the option set within your "/etc/apache2/apache2.conf":
```
DirectoryIndex **index.php** index.htm index.shtml index.html index.cgi index.pl index.xhtml index.php3
```
If you change this just issue the command:
```
sudo /etc/init.d/apache2 restart
```

---

