---
title: "startup scripts?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by jestinjoy on 2009-01-20
Anyone please tell which script is executed before bashrc file when we login to text mode( I made ubuntu to boot into text mode by default)

---

### Post by ibutho on 2009-01-20
If you are referring to bash startup files, then take a look [here]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_02.html").

---

### Post by jestinjoy on 2009-01-20
In text mode after the login we are told about the last login time,present time,some info about ubuntu.......After that the bash prompt comes up.I want to know about the file that is executed just after the login process.......

---

### Post by ibutho on 2009-01-20
That information is obtained from various files. The info about last logins is got from /var/log/lastlog. Release info is in /etc/issue and other messages are in /etc/motd

---

### Post by jestinjoy on 2009-01-20
I tried to edit the /etc/motd file..But in the next system reboot the file is changed to the old one..............This file is rewritten during each reboot?

---

### Post by ibutho on 2009-01-20
AFAIK, you should be able to edit it and your changes should not be overwritten. Maybe try editing /etc/motd.tail.

---

### Post by emarkd on 2009-01-20
This is a long-running issue for some people.  Editing the motd.tail file like ibuttho suggested is the way to get around it.  If I remember correctly, I think the motd file can be modified by the /etc/init.d/bootmisc.sh script while booting.

By the way, there's lots of scripts in /etc/init.d/... that run before bash starts

---

### Post by jestinjoy on 2009-01-20
Thanks............../etc/motd.tail is the file to be edited........otherwise it will move back to the old stage:D

---

