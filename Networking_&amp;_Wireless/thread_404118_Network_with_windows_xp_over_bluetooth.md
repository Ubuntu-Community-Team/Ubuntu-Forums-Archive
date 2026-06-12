---
title: "Network with windows xp over bluetooth"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by crazyfish on 2007-04-08
Hi, I'm trying to build a LAN between my ubuntu desktop and my windows xp Thinkpad using bluetooth. Well, I want to make the desktop a gateway to internet so that  the laptop can move around in my small bedroom.

On the desktop, I operated as someone did to set up all-linux PCs LAN. I installed bluez-pin, bluez-utils, ppp packages. The usb bluetooth adapter can then be seen with command:
fish@Fishost:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:11:B1:07:A2:CE ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:395 acl:0 sco:0 events:17 errors:0
        TX bytes:317 acl:0 sco:0 commands:17 errors:0

After that, I ran command:
fish@Fishost:~$ pand --master --listen --role NAP

On the laptop, I can find the Network Access Point on the desktop. But when I clicked the icon of the access point to establish the connection, an network link failure appeared with severity error prompt. (I can successfully pair my bluetooth phone with this laptop so I suppose all the necessary services are ready.)

Do you have any suggestions? Thanks.

---

### Post by Topogigi on 2007-04-08
sudo chmod +s /usr/bin/pand

then reestablish the connection

---

### Post by crazyfish on 2007-04-08
Can't get connected still. It seems the laptop can not pair with ubuntu :confused:

---

