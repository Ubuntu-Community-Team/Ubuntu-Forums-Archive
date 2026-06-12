---
title: "Ubuntu 8.04 upgrade completely broke my wireless connection"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by ChrisMcCann on 2008-05-10
This is the worse upgrade yet.  Its not getting better, its degrading.  I used to have wireless work almost flawlessly.  I have tried all sorts of
things to get my WG511T to work with no avail.  The Atheros restricted drivers don't work.  The ndiswrapper works and sees the PCI card, but
the association does not succeed.  I tried using the iwconfig and ifconfig
command lines, again there is nothing that is working.

I have a router with WPA 2 using TKIP as the encryption method.  Can anybody
suggest something or my laptop is going to be useless since I can't roam
any longer.  I will have to plug in the wired interface.  :mad:

Does anyone have any suggestions?

---

### Post by ChrisMcCann on 2008-05-11
I solved it by using the madwifi drivers.  I added the following lines
to /etc/init.d/networking

under the start) case statement I added,

modprobe ath_pci
modprobe wlan scan_sta

I am wondering if I should add these 2 lines to the restart) case statement?

Looking forward to hearing a solution to why I get "Interface does not exist" when using the Network Tools program.  After hitting the configure
button and typing my password, I get this message.  I see others have already posted this so I will check back.

---

### Post by littlewild on 2008-05-23
> **ChrisMcCann said:**
> I solved it by using the madwifi drivers.  I added the following lines
to /etc/init.d/networking

under the start) case statement I added,

modprobe ath_pci
modprobe wlan scan_sta

I am wondering if I should add these 2 lines to the restart) case statement?

Looking forward to hearing a solution to why I get "Interface does not exist" when using the Network Tools program.  After hitting the configure
button and typing my password, I get this message.  I see others have already posted this so I will check back.

I am having the same problem. Isn't the madwifi driver included in the restricted package?

I just can't seem to get modprobe ath_pci to work. Modprobe can't find the module.

---

### Post by littlewild on 2008-05-23
A clean installation of Ubuntu 8.04 fixed the problem. The card now works right from start.

Guess the upgrade process from 7.10 to 8.04 screwed up some of the paths/modules.

---

