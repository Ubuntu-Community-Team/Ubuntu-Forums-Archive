---
title: "[SOLVED] Wireless Networking Setup Help Please"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by daveerickson on 2007-04-12
I am attempting to setup wireless networking on 6.10 using a Linksys wmp11 v2.7 card. I have read that some people need to use ndiswrapper for it to work. I ran lspci -v | less and iwconfig and below are the results:

lspci -v l less

01:08.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Co
ntroller (rev 02)
        Subsystem: Linksys Unknown device 4301
        Flags: bus master, fast devsel, latency 32, IRQ 209
        Memory at e7004000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I am connected to my wireless network through WinXP:redface: so I know it is up and running. I do notice that my ESSID is "" and that is not correct. When I run the Network Configuration I set it to my network name and it does not seem to be taking that setting:x . Any way to force that setting?

It appears to me that Ubuntu sees the card, is that correct? Is there something else I can try to get this to work? I am willing to run any commands and return any info I can. I want to ditch XP for GOOD!:D 

Thanks for all your help.

D

---

### Post by sabi on 2007-04-12
You are correct. Your driver is loaded and recognized. What the iwconfig output shows is that the wireless card is not associated with the access point.

Are you running network manager? Do you have a network icon in the upper right portion of the system tray? If so, simply right click and check to see if wireless networking is checked. Then, left click on the icon and select the access point to connect with.

Hope this helps...

Sabi

---

### Post by happy-and-lost on 2007-04-12
Yay. Oh the fun I had getting my Broadcom wifi card working. I'm afraid I can't find the thread where I found my answer, but the [bcm43xx]("http://bcm43xx.berlios.de/") project was very useful. Take a look at [this]("http://www.linuxquestions.org/linux/answers/Networking/HOW_TO_install_the_Broadcom_bcm43xx_Driver_in_Debian_Linux_and_enable_WPA_Encryption") page too. If I find the page which solved my problem, I'll post it. Good luck.

EDIT: Your driver may not be working. Post the output of *dmesg | grep bcm*

Another: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by daveerickson on 2007-04-12
Thanks for the quick responses both of you!:) 

sabi, I don't have network manager in my system tray. The way I have been trying to connect to my wireless network is through System -> Administration -> Networking. There is a checked box next to Wireless Conenction and the correct essid. However still not working. Would network manager have better luck? If so how should I install it?

happy-and-lost, Here is the output from running dmesg | grep bcm:
[17179588.420000] bcm43xx driver
[17179735.972000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[17179735.976000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

I will check out the links you sent. I am confident I will get this working! :D 

D

---

### Post by wetland on 2007-04-12
I used this how to for wifi-manager [Link]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") Once you get your card working give it a shot. Also if you use WPA you will be all set.

---

### Post by happy-and-lost on 2007-04-12
As I thought, the drivers aren't working. The firmware cutter should do just the trick.

---

### Post by daveerickson on 2007-04-12
I am MOST pleased! :D 

I followed the instructions from help.ubuntu.com site you recommended and things are now working! Thank you so much for all of the input! And thank you happy-and-lost! You guys rock!

D:KS

---

