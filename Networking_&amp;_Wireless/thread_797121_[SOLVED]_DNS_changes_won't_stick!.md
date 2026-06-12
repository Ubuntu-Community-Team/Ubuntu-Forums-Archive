---
title: "[SOLVED] DNS changes won't stick!"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by King_Critter on 2008-05-17
I'm trying to add the OpenDNS nameservers to /etc/resolv.conf, but the file keeps reverting to its default state. I've tried both manually editing the file, and changing through network-admin. If I use network-admin, the changes stick until a few seconds after I close the window. If I edit them manually, it stays for a few seconds after I save the file.

Any ideas?

---

### Post by pjnsmb on 2008-05-17
Guess you have to be root to edit it ?

pjnsmb

---

### Post by King_Critter on 2008-05-17
Yes, I have to use sudo to open the file or make any changes in network-admin. I should think that's a given, seeing as how it's not in my home folder...

---

### Post by nicedude on 2008-05-17
Try this

sudo chmod +w+w /etc/resolv.conf

and see if with this it won't stay edited
gksudo gedit /etc/resolv.conf

---

### Post by helgman on 2008-05-17
I've had problems with changing DNS settings and using DHCP ... every time the DHCP client "speaks" to the DHCP server the settings are reverted, but this usually is not within a mater of seconds but usually longer (depending on lease time).

Hrm ... mine don't change in a matter of seconds, no (just tested it).

I do remember reading a thread where someone had a similar problem, just don't remember where and when and if they fixed it ... guess that's not all to helpful.

A quick search in the forum gives a few tips.

A) If you control the DHCP server (might be a home router) see if you can change the configuration so that it gives you the DNS-servers it's using rather than itself as DNS-server (or make the changes so that it too uses the servers you want to use if it already serves you the servers it's using).

B) I've found [this thread [How-To Stabilise your DNS addresses]](http://ubuntuforums.org/showthread.php?t=282034) that does some changes to the dhclient configuration. Just read up on exactly what the changes does before you do them.

C) I think I saw one or two solutions in [this thread [DNS server]](http://ubuntuforums.org/showthread.php?p=1960622#post1960622) and again, just make sure you understand what the changes do before you apply them.

Good Luck!

Helgman

---

### Post by King_Critter on 2008-05-17
Helgman, the solution in your second link worked like a charm -- thank you *very* much!

---

