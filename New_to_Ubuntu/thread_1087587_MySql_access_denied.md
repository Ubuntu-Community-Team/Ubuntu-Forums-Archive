---
title: "MySql access denied"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by anujs on 2009-03-05
Hi all....

I am able to work on mysql server through ssh. Also I edited the bind-address to my server ip. when i visit mysql at my web browser, I get following error:

"Access Denied.
Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect." 

port is 3306, what else required in my.cnf?
How to solve it?

---

### Post by Brandon.Viking on 2009-03-05
It might be that you have bound the MySQL server software to only listen to the IP Address on the eth interface, which means that if the software which is attempting to access MySQL via the "localhost" or 127.0.0.1 address which is not responding as you have only told MySQL to listen to the server IP address. Perhaps using the command 'netstat -na | more' will allow you to see what MySQL (look for port 3306) is listening on. Also 'sudo netstat -nap | more' will give you the process associated witht the connection too.

Help that helpsl.

---

### Post by anujs on 2009-03-06
it listen....also i am able to work at console.

problm is: when on web browser i type [http://server-ip:](http://server-ip:) 3306, it shows :

Access Denied.

Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect. 


what to do? my tomcat work fine.....even php too. what with mysql?

---

### Post by anujs on 2009-03-06
Problem solved.....

i am new to linux..mysql....thats why?

I wanted phpmyadmin actually that give GUI through browser.
what i did, installed phpmyadmin with "sudo apt-get install phpmyadmin"

now working fine.....:-)

---

