---
title: "How to setup Telnet and FTP (VSFTP)"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by henkasdf on 2007-10-03
Hi Everyone,

How do I install telnet and vsftp on Feisty Fawn.  I am new to linux.  A few suggestions would be appreciated.

Thanks

---

### Post by dmizer on 2007-10-03
don't know much about vsftpd but i do suggest you have a look at the third link in my sig for proftpd

instead of telnet, use ssh.

a good ssh client for windows is putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

if you need to transfer files from windows over ssh, you can do so with cygwin (an alternate linux shell client for windows): [http://www.cygwin.com/](http://www.cygwin.com/)

ssh will give you an encrypted secure connection to your server, where tellnet will not.

---

### Post by henkasdf on 2007-10-03
Hi, thanks for the reply,

I have a fresh installation of Ununtu 7.04 and I cannot run the "sudo apt-get install proftpd gproftpd" command.

I get the following error:  payday@Ubuntu:~$ sudo apt-get install proftpd 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
payday@Ubuntu:~$

Any solution.

Thanks

---

### Post by dmizer on 2007-10-03
yup.  close synaptic package manager before running the command in command line.

---

### Post by henkasdf on 2007-10-03
Thanks,

But the package manager is closed.  Still same problem.

---

### Post by dmizer on 2007-10-03
add/remove applications?  maybe update manager?  something like that.

if you still have the problem, post the output of:
```
ps -ax
```

---

