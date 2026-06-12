---
title: "ACER Aspire 4810T ... CD/DVD not working"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by vmsda on 2011-03-13
I am running Ubuntu 10.04, with kernel 2.6.32-29-generic-pae (32-bit); the CD/DVD is not working: the drawer does not open when I push the button, and the drive is not mounted even though the icon does show up in Places/Computer.

I know there is no hardware problem because it works on in Windows 7 (I have a dual system installation).

Is there a solution or is it safer to go back to a previous version of Ubuntu?

Thank you in advance.

---

### Post by Wobblybob on 2011-03-13
try opening a terminal and entering

ls -l /dev/cdrom

does this list your drive like this

lrwxrwxrwx 1 root root 3 2011-03-13 22:56 /dev/cdrom -> sr0

does it open when you issue;

eject /dev/cdrom

---

### Post by vmsda on 2011-03-14
Thank you for your prompt reply, Wobblybob.

AAA. Here's the output from the terminal I opened:
```
vasco@vasco-laptop:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-03-14 08:49 /dev/cdrom -> sr0
vasco@vasco-laptop:~$ eject /dev/cdrom
vasco@vasco-laptop:~$ eject /dev/cdrom
eject: unable to find or open device for: `/dev/cdrom'
vasco@vasco-laptop:~$ eject /dev/cdrom
eject: unable to find or open device for: `/dev/cdrom'
vasco@vasco-laptop:~$ ls -l /dev/cdrom
ls: cannot access /dev/cdrom: No such file or directory
vasco@vasco-laptop:~$ 

```
As you can see, the "ls" display looks like what you expected. Then I tried to eject and it worked!!! Then I closed the drawer and everything went back to square one.
 
BBB. Later, I decided to do something original. Restarted the system and made sure the "ls" was ok; then ejected, inserted a disc, burned it, took it out and closed the drawer. Tried the "ls" command again and it was ok; then ejected /dev/cdrom, closed the drawer but this time decided to make sure the drive stopped; tried the eject again and it worked!!! And it works ok no matter how many times I repeat this operation.

CCC. My keyboard features an eject key on the top right hand side; this does not work with Linux. In fact, even if everything is working ok as per described above, if I touch the eject key then, in response to the "ls" command I get the familiar "ls: cannot access /dev/cdrom: No such file or directory".

Crossing my fingers that you may have an explanation for this - but at least the worst is over!. Thank you again.

---

