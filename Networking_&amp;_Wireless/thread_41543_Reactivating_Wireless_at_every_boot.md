---
title: "Reactivating Wireless at every boot"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by Flockmeal on 2005-06-13
I've set up my broadcom wireless card correctly with ndiswrapper and it connects to my network perfectly with WEP enabled. However, every time I boot up I have to open the Network Settings in Gnome and activate wlan0. What can I do to make this activate at boot automatically?

---

### Post by AMP on 2005-06-13
[QUOTE=Flockmeal]I've set up my broadcom wireless card correctly with ndiswrapper and it connects to my network perfectly with WEP enabled. However, every time I boot up I have to open the Network Settings in Gnome and activate wlan0. What can I do to make this activate at boot automatically?[/QUOTE]
 Try sudo ndiswrapper -m  that should write the appropiate modprobe for startup.

May i ask how your broadcom is set up i cant get mine to work.

---

### Post by byen on 2005-06-14
[QUOTE=AMP]
May i ask how your broadcom is set up i cant get mine to work.[/QUOTE]

AMP... if you are looking for a ndis-wrapper/broadcom walkthrough.... this is the page yu shud be looking at...goodluck!

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by CloudNine on 2005-06-14
I'm currently working on a Broadcom driver by the way, but no-one seems to be bothered much from the posts I've made about it. It'll support all 802.11B and G Broadcom chipsets once it's done. You can contact me at [email]mwhitworth@gmail.com[/email] if you'd like to test :)

---

### Post by AMP on 2005-06-14
[QUOTE=byen]AMP... if you are looking for a ndis-wrapper/broadcom walkthrough.... this is the page yu shud be looking at...goodluck!

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)[/QUOTE]
 Thanks im doing a fresh install to run this, as i have messed up a .deb and .tar install b4 compiling!

---

### Post by Flockmeal on 2005-06-14
Ndiswrapper is in /etc/modules so my wireless card is coming up at boot, but when I log in and gnome comes up the network monitor in the top right corner says I'm disconnected, so I must click on it, click on config, and activate wlan0. I think this is because "Starting Network Interfaces" fails at every boot. What should I do? I'm a horrible linux newbie.

---

### Post by byen on 2005-06-15
AMP - you do not have to do a fresh install at all..in the same thread the author has specified certain commands that yu can type to fix all previous work-arounds. well.... just letting yu know.
Flockmeal - the same goes to your Q? too. I think this Q was answered in one of the replies.

---

### Post by Mr. Electric Wizard on 2005-06-16
Hey guys, 
what is the missing link between doing modprobe ndiswrapper, and getting the driver to show up in "Networking"?
The driver is installed, what's next?

---

