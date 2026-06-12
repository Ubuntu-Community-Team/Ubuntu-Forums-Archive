---
title: "internet problem"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by damansandhu on 2007-09-15
hi guys ,
i am using ubuntu 7.04 fiesty , my pppd was working properly and now it dont work , please help me out . i have dsl connection .

i think this my help

aman@Ultimate:~$ pppoeconf
About to execute /usr/sbin/pppoeconf.
This command needs root privileges to be executed.
enter root passwd:
Password:
su: Authentication failure
Sorry.
Incorrect password or command failed. Try again? (y/n)n
daman@Ultimate:~$ sudo pppoeconf
Password:
Plugin rp-pppoe.so loaded.
daman@Ultimate:~$ poff
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ poff dsl provider
/usr/bin/poff: I could not find a pppd process for provider 'dsl'. None stopped.
daman@Ultimate:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ pon dsl provider
The file /etc/ppp/peers/dsl does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory.
daman@Ultimate:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ plog
Sep 16 02:42:17 Ultimate pppd[6201]: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
Sep 16 02:42:38 Ultimate pppd[6213]: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ poff
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$

---

### Post by damansandhu on 2007-09-15
i need help

---

### Post by damansandhu on 2007-09-16
help me out

---

### Post by abhisheklovesa on 2007-09-16
use command        sudo  pppoeconf       instead of  < pppoeconf >
this will give u a root login.

---

### Post by damansandhu on 2007-09-18
i think nobody is going to help , guys i cant use internet in ubuntu , plz help me if you can

---

### Post by damansandhu on 2007-09-18
i have checked the dsl router connection , its properly connected and i even can browse my router by typing "192.168.1.1" in firefox . when i type "sudo pon dsl-provider" in terminal , it says that some file is loaded , means that internet is connected , but i cant acess internet , it was working fine few days ago , i dont know what happened now .

---

### Post by damansandhu on 2007-09-18
help plz

---

