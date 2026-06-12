---
title: "Cutting off the internet at a specific time (teenager to bed)"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by netopyr on 2007-10-14
Hello,

This is a rare question how to make something NOT to work. :-)
I had this working with SuSE 10.1 but now I bought myself a notebook (Dell Inspirion 6400 with ubuntu preinstalled) and my daughter received my desktop with a fresh kubuntu 07.04 installation.

Goal:
To make the Internet unusable at a specific time so that my daughter can be in the internet while I already go to bed.

Environment:
The PC of my daughter has its internet connection via ethernet cable and the IP adress comes via DHCP from the router. My daughter does not know the password for her linux account.

Solution so far under SuSE 10.1:
I identified the command to disconnect the connection [FONT="Courier New"]'ifconfig eth0 down'[/FONT] and I put this into a file called 'jennyende'. Then I made two entries within /etc/crontab
	[FONT="Courier New"]15 22 * * 0,1,2,3,4 root /bin/jennyende
	45 23 * * * root /bin/jennyende[/FONT]
On days when there is school taking place next morning then at 22:15 the internet disappears. Generally on all days at 23:45 there is definetely the end of the internet.

As said this worked perfectly under SuSE 10.1 but it does not work under kubuntu 07.04. Has anybody a tip why? - e.g. a new feature that realizes the lack of the internet connection and reestablishes it automatically or something like that? Thank you very much for your hints in advance.

---

### Post by A$h X on 2007-10-14
[FONT="Tahoma"]What router do you have? I have a linksys WRT54GS and it has all sorts of options to limit internet access to specific IP's, at specific times etc.
Rather than tamper with samba, maybe it would be easier to use the router setup? Hope that helps. [/FONT]

---

### Post by hugoheden on 2007-10-14
Hmm, I wonder what we'll answer when your daughter comes here and asks about her weird internet connection that disappears at 22:15 every night :-)

---

### Post by milosz.galazka on 2007-10-14
Try this one
```
/etc/init.d/networking stop
```

---

### Post by s3a on 2007-10-14
I'm glad I'm not your daughter (even though I'm a boy)...

---

### Post by milosz.galazka on 2007-10-14
> **hugoheden said:**
> Hmm, I wonder what we'll answer when your daughter comes here and asks about her weird internet connection that disappears at 22:15 every night :-)

just reboot ;p or mess up with single user mode ;p

---

### Post by netopyr on 2007-10-19
just wanna say 'thanks for your help' - 'networking stop' seems to work ;-)

My router (a FritzBox 3070) unfortunately does not support the feature to limit access by time. The more expensive version support this children security. This would have been the best method since the intelligence would have been outside  of my daughter's machine.

---

