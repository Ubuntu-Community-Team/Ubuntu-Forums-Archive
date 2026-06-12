---
title: "I cant start MYSQL in Lucid"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by ynwa-red on 2010-05-19
Hi,  

I am new to Linux/ Ubuntu and all this fancy stuff.   

I have installed LAMP server onto my Lucid virtual machine.   

I have managed to figure out how to start Apache2 and put files into the var/www folder using sudo mv filename etc/. 

The problem i am having now is trying to start Mysql  

i have tried just using 

sudo /etc/init.d/mysql start

but when i click enter its says 

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql

so i have used   

jon@jon-desktop:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.102" (uid=1000 pid=2945 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

Can anyone help please because i havent got a clue what any of this means . 

Many thanks 

J

---

### Post by proxess on 2010-05-19
sudo service mysql start ??
sudo start mysql ??
Also, try bum.

Edit: sorry, that came out wrong. bum as in Boot-Up Manager. It's a GUI app.

---

