---
title: "Cannot get Linksys/Broadcom BCM43XG (rev 01) to work in 8.04"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by RustyWyatt on 2008-05-10
Hi Folks,

I am trying to get my Linksys/Broadcom PCI wireless card:
 
lspci | grep Broadcom\ Corporation02:03.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

To work in 8.04.

I have followed the following instructions including all of the fixes:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

Unfortunately I still do not &#8220;see&#8221; my card.

When I do the &#8220;start over&#8221; fix I get the following error at:
tom@Mythbuntu:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

I have spend the evening trying to get the card working and may have really trashed 8.04 by trying every todo I could find...

I still cannot see my wireless card ;-(

All info GREATLY appreciated!

Thanks,
Tom

---

### Post by superprash2003 on 2008-05-10
hope this helps [http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html)
 you might need to connect your pc to a wired connection.. as many steps require internet.

---

