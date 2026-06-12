---
title: "acer aspire one (wireles problem)"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by alexeyhurricane on 2008-11-05
just installed UBUNTU 8.04.1 on my acer aspire one and cant get wireless on it , i dont have wired connection to it only wireless that is the problem
pls help how can i fix it with out wired connection

---

### Post by Fanless_Puppy_Fan on 2008-11-05
WICD

[http://ubuntuforums.org/showthread.php?t=905983](http://ubuntuforums.org/showthread.php?t=905983)

---

### Post by The Cog on 2008-11-05
WICD should give you a fighting chance provided your wireless drivers are working. You can download a .deb file from here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) which can be installed just by double-clicking it. Use another PC to downliad it and put it on a USB stick. But you will have to uninstall network-manager first with this command: **sudo aptitude remove network-manager**

---

### Post by ullix on 2008-11-07
Why did you install 8.04 after 8.10 came out? First, make your life easier and install 8.10, then install the linux-backports-modules-intrepid, and reboot. Wireless should work.
May need some cleanup using the Hardware-Drivers utility: have only the "Support for 5xxx series of Atheros 802.11 wireless LAN cards" activated. 
If not, try the wireless switch on the front ONCE, and see if it had been switched off accidentally.

---

### Post by ullix on 2008-11-07
Why did you install 8.04 after 8.10 came out? First, make your life easier and install 8.10, then install the linux-backports-modules-intrepid, and reboot. Wireless should work.
May need some cleanup using the Hardware-Drivers utility: have only the "Support for 5xxx series of Atheros 802.11 wireless LAN cards" activated. 
If not, try the wireless switch on the front ONCE, and see if it had been switched off accidentally.

---

