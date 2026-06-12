---
title: "I'm doing it wrong: need help with a remote share"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by TechDragon on 2010-05-14
Ok, I have a computer at home that I want to access from work, the home computer is Ubuntu 10.04 and the work computer is Windows 7.  I have set up two shares on my home computer one with guest access sharing and the other that requires my user name and password. 

Heres the deal, the share that is set up to guest access, I can access, no problem.  But it doesn't seem very secure, anyone with my IP can see those files apparently.  

I want to utilize the share that requires my user name and password, and when I click on it Windows pops up the box for me to do so, but keeps the work domain prevalent, I did some digging and found that Ubuntu apparently has put this file under the domain "workgroup" so I try

workgroup\name
password

Then click ok but recieve "windows cannot access  ipaddress\share name"

so i know it is seeing it, I know it is asking for the user and password, I don't know why it wont let me access it.  It lets me access the wide open share but not the password protected one.

Help please

---

### Post by cariboo on 2010-05-14
If you are sharing directories over the internet please don't use Samba, that is almost a guarantee that your computer will be cracked.

If you want to access your system remotely ssh is much more secure. For an openssh-server howto, have a look [here]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html").

Once you have the server setup, use something like winscp or filezilla, to access files.

---

