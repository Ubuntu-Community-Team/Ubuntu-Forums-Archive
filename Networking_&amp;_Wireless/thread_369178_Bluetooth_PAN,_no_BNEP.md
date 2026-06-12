---
title: "Bluetooth PAN, no BNEP????"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by _ivan_ on 2007-02-24
Hi, i am trying to set up a wireless connection between 2 PCs with use of bluetooth. I have followed the guid on this site.

[http://gentoo-wiki.com/HOWTO_The_host-to-host_Bluetooth](http://gentoo-wiki.com/HOWTO_The_host-to-host_Bluetooth)

My problem is that when running a NAP server using command #pand --listen --role NAP
there is no bnep0 created. i have imported the module with command #modprobe bnep is it the way it should bee done. 

So as a summery this is what i have done:
#modprobe bnep
#pand --listen --role NAP

Do i have to import anything else in the kernel or somehting else?

---

### Post by info2 on 2007-03-14
As far as i know , the bnep - Device will be created after a pairing occured. 
For example, if your PC "a" acts as NAP, bnep0 will be created after PC "b" is connected.

---

