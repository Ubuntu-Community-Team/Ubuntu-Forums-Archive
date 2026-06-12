---
title: "Cant Connect to MySQL using PHP"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by mevets on 2010-04-21
I install apache2, php5 and mysql-server. I am now trying to connect to the database with this code
[PHP]
define('HOST', 'localhost');
  define('USERNAME', 'www-data');
  define('PASSWORD', 'mypass');
  define('DB', 'smccart6');
  $connect = mysqli_connect(HOST, USERNAME, PASSWORD, DB) or die('<p>Could not connect to the database.</p>');
[/PHP]
I tried to do it initially with root and the root users password but php told it failed to connect using the user www-data. So, I created a user named www-data using phpmyadmin. Now it tells me that I am still trying to connect with www-data and NO password although it is definetly being supplied.

Is there an answer to this problem?

---

### Post by _0R10N on 2010-04-21
I noticed that you're missing the php5-mysql package...

Kind regards!

_0R10N >>

---

