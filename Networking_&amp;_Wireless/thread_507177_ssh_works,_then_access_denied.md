---
title: "ssh works, then access denied"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by ecomber on 2007-07-22
I installed Feisty Server (may be significant as there is tighter security I understand)  on a headless box using  a serial port. I then installed openssh-server and connected from another machine on the LAN.

Superb, it worked, and worked for several days.

Then one fine day it didn’t work any more, giving ‘access denied’ (there may have been a reboot in the meantine). I tried everything but could not find the reason.  I installed telnetd, but it wouldn’t work either,

Then I removed openssh-server completely and installed it again. 

Lo! It works again.

Any ideas?

There are two issues – 

What was blocking it now, and ...

if something like the firewall was blocking it, is there a loophole issue with it being open when first installed..

Grateful for any help.

Eddie.

---

### Post by dougfractal on 2007-07-22
try 
[http://doc.gwos.org/index.php/SecureSSH#Securing_OpenSSH](http://doc.gwos.org/index.php/SecureSSH#Securing_OpenSSH)

---

