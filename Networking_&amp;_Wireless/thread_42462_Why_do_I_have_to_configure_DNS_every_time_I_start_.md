---
title: "Why do I have to configure DNS every time I start up my PC"
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by John O'Connor on 2005-06-17
Every time I start my PC it loses its DNS settings. I change them and /etc/resolv.conf shows the correct IP numbers for my ISP's DNS servers. But if I restart my pc they are no longer there and instead /etc/resolv.conf show something like the following:
 nameserver 192.168.62.1

Where can I set some option that makes sure that my settings do not get lost?

---

### Post by jerrykenny on 2005-06-17
I wonder if your modem is trying to use DHCP whilst you're trying to use static addresses ?



Anyway heres the link for the Gentoo networking instructions

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=3](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=3)



Good luck.

---

### Post by John O'Connor on 2005-06-17
Thanks for your quick repy, but I have tried everything in Gentoo and Debian guides.
I re-tried Ubuntus network setup, set my DNS addresses, checked /etc/resolv.con and they were correct. Then I re-booted and the  /etc/resolv.conf was changed back to 192.168.... etc.  I gave up.
I have re-booted and instead of re-booting Ubuntu have gone back to Suse 9.2. I have looked at /etc/resolv.conf in Suse and the two DNS entries are correct. 

So my question is: Where and why does Ubuntu Linux change them?

(SUSE and Ubuntu are both on exactly the same hardware, alternatively re-booted, SUSE does not change my settings but Ubuntu does change them every time. And bye-the-way Windows on the same PC gets it right every time.)

---

### Post by desdinova on 2005-06-17
tu dialup[QUOTE=John O'Connor]Thanks for your quick repy, but I have tried everything in Gentoo and Debian guides.
I re-tried Ubuntus network setup, set my DNS addresses, checked /etc/resolv.con and they were correct. Then I re-booted and the /etc/resolv.conf was changed back to 192.168.... etc. I gave up.
I have re-booted and instead of re-booting Ubuntu have gone back to Suse 9.2. I have looked at /etc/resolv.conf in Suse and the two DNS entries are correct. 

So my question is: Where and why does Ubuntu Linux change them?

(SUSE and Ubuntu are both on exactly the same hardware, alternatively re-booted, SUSE does not change my settings but Ubuntu does change them every time. And bye-the-way Windows on the same PC gets it right every time.)[/QUOTE]

How did you setup your dialup connection - I get the feeling you may need to look at your network cards config if it insists on making 192.168.0.1 a DNS server

---

### Post by dissident on 2005-06-18
I'm just a little ol' Linux n00b, but I think you can lock your DNS values by doing a **sudo chattr +i /etc/resolv.conf** as seen in [this](http://ubuntuforums.org/showthread.php?t=5690) guide. Hope that helps.   :grin:

---

### Post by John O'Connor on 2005-06-18
[QUOTE=jerrykenny]I wonder if your modem is trying to use DHCP whilst you're trying to use static addresses ?

[/QUOTE]

I have changed my setup to use Static address - I use a LAN with an unbranded Router connected to Netopia DSL modem. Now that I have changed my network card to use static IP, Ubuntu no longer modifies my /etc/resolv.conf file at boot time.

Thank you all for your replies. (And now on to fix my ATI driver problems - that appears to be much more of a minefield, but where in Windows could you have so much fun??)

---

### Post by Seer on 2005-06-20
[QUOTE=John O'Connor]I have changed my setup to use Static address - I use a LAN with an unbranded Router connected to Netopia DSL modem. Now that I have changed my network card to use static IP, Ubuntu no longer modifies my /etc/resolv.conf file at boot time.

Thank you all for your replies. (And now on to fix my ATI driver problems - that appears to be much more of a minefield, but where in Windows could you have so much fun??)[/QUOTE]
 There is a script that runs at start up that rewrites you resolv.conf file every time you boot up if you are using dhcp. You need to open it and comment out the part of the script that does it.... I know I'm a 3 day old noob and have been going mad trying to resolve my slow browsing issues (which I will post about in a minute)

Looking for link I found now.................

.....

.........

crap I can't find the link here at work - I'll try to post later!!

Yay found it again :) !!!! Worth a sticky I reckon :)

[http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf](http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf)

---

### Post by John O'Connor on 2005-06-24
[QUOTE=Seer]There is a script that runs at start up that rewrites you resolv.conf file every time you boot up if you are using dhcp. You need to open it and comment out the part of the script that does it.... I know I'm a 3 day old noob and have been going mad trying to resolve my slow browsing issues (which I will post about in a minute)

Looking for link I found now.................

.....

.........

crap I can't find the link here at work - I'll try to post later!!

Yay found it again :) !!!! Worth a sticky I reckon :)

[http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf](http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf)[/QUOTE]


Thank your Seer - that works. I guess you deserve 2 sticky buns and at least another CUP OF UBUNTU!!.

---

### Post by Seer on 2005-06-24
Yay!! My first write answer!!

 \\:D/

---

