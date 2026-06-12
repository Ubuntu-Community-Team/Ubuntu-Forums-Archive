---
title: "Dwl-g650"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by wireddad on 2006-12-09
Hello,

I have a D-Link AirPlus Xtreme G DWL-G650 vB4.  It worked fine using LiveCD, and initial Ubuntu install to the HD.  At first boot, it alerted me that there are new updates.  Said ok and updates started.  Now wireless card will not work.  Thoughts?  Thanks.

I am new to linux.

---

### Post by FrodoB on 2006-12-09
It sounds like you are using the Alternate CD. If so the solution is simple:

1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.


If this is not the problem, then report back to the forum please.

---

### Post by wireddad on 2006-12-09
Thank you.  I will try your suggestion in a bit.

---

### Post by wireddad on 2006-12-09
Here is what it shot back at me:

wireddad@pavilion:~$ sudo apt-get install linux-restricted-module-'uname -r'
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-module-uname -r
wireddad@pavilion:~$

I am sure I have mis-understood.  ](*,)

---

### Post by FrodoB on 2006-12-09
You have to us back single quotes, the key with the ~ on the top just under the ESC key.

---

### Post by wireddad on 2006-12-09
Huh?  What is us back?  Sorry I am not linux literate.

---

### Post by spd106 on 2006-12-09
He means the back quote [http://www.computerhope.com/jargon/b/backquot.htm](http://www.computerhope.com/jargon/b/backquot.htm) rather than the normal one.

i.e. ` rather than '

or enter linux-restricted-modules-2.6.17-10-generic, instead.

---

### Post by wireddad on 2006-12-09
Ah!  Will do.

---

### Post by wireddad on 2006-12-09
Did not work.  Said could not find package.  I'd tried both suggestions.

---

### Post by wireddad on 2006-12-09
Loaded Kubuntu and all seems to be working good.  Time to go learn some survival linux.  Thanks.

---

