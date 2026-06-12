---
title: "cannot connect mysql service from other machine"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by MHL on 2006-08-06
Hi, I am pretty new to Ubuntu, and I have setup the mysql server, but I can't connect to mysql server from other host. the problem is I think ubuntu is blocking the port 3306. When I do "netstat -na |grep "LISTEN"" it shows mysql is listening on port 3306. I have setup a mysql to able connect a user from other host.

is Ubuntu running some kind of firewall software?


thank you very much.

---

### Post by sitedesign on 2006-08-07
Take a look at /etc/mysql/my.cnf

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1

change the bind line to your network address or I think you can dummy it out with a # 
then restart the mysql server with
sudo /etc/init.d/mysql restart
or something, use TAB completion.

---

### Post by ncsufctl on 2006-08-08
I am having a similar problem.  I've installed mysql, and as I was trying to set a password for root, I get the following error:

mysqladmin: connect to server at 'Linuxserver-ftl.fis.ncsu.edu' failed
error: 'Host 'Linuxserver-ftl.fis.ncsu.edu' is not allowed to connect to this MySQL server'

I've already commented out the bind-address line in /etc/mysql/my.cnf, and I also tried setting it to the address of my server itself.

In a tutorial for setting up a LAMP server on howtoforge.com, it says use the following lines for setting the mysql root password:

mysqladmin -u root password yourrootsqlpassword
mysqladmin -h server1.example.com -u root password yourrootsqlpassword

The first line ran with no problem.  I replaced "server1.example.com" in the second line with "Linuxserver-ftl.fis.ncsu.edu" and the error I posted above is what I get.  Any ideas on how to correct this issue?  Thanks!

Brian

---

### Post by sitedesign on 2006-08-08
instead of your hostname you will need to use localhost or 127.0.0.1

By default you will only be able to connect for root from localhost

Hope that helps

---

### Post by ncsufctl on 2006-08-09
thanks, sitedesign.  what the problem was is that i was trying to remotely connect to mysql via root, which it obviously does not allow.  i created another mysql user and was able to login remotely with no problem.

---

