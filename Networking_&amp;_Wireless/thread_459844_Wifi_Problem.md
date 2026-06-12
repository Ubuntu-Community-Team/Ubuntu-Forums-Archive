---
title: "Wifi Problem"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by PKP32 on 2007-05-31
I have recently loaded Ubantu 6.06 (kernel 2.6.15-23-386) on my Dell Inspiron 6400 laptop in Dual boot mode. My Card details & driver - as per Windows is
1. Wireless 3945ABG Network Connection
       c:\windows\system32\drivers\w39n51.sys      (Provider -Intel Corp)
       c:\windows\system32\w39MLRes.dll 
       c:\windows\system32\w39NCPA.dll

2. BROADCOM 440X 10/100 INTEGRATED CONTROLLER 
       C:\windows\system32 \drivers\bcm4sbxp.sys

3. 1394 Net adapter
       C:\ windows\system32\drivers\nicl394.sys

4. BT LAN ACCESS SERVER DRIVER
       C:\ windows\system32\divers\btwdndis.sys   (Provider - broadcom) 

In Ubantu Terminal  it displays (lspci )
Ethernet Controller 
0000: 03:00.0   Broadcom Corporation BCM 4401-BO 100 BASE TX (rev 02)

My Wireless network refuses to work! 

Please Help

---

### Post by shibu on 2007-05-31
Try this .... :)


apt-get install  wpasupplicant  network-manager-gnome  network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” 

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file.

Reboot your system and select network manager and then wireless network.

---

### Post by PKP32 on 2007-05-31
Dear Shibu,
Thanks for the help.

let me try

Pramod

---

### Post by PKP32 on 2007-06-01
Dear Shibu, 

My Wireless network is still not working, I tried your suggestion.
Any other method? 

Pramod

---

