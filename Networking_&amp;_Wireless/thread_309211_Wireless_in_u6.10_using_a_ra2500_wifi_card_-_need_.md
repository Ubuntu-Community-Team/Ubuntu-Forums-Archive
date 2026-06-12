---
title: "Wireless in u6.10 using a ra2500 wifi card - need to manual configure on each boot!"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by bmatteo on 2006-11-29
[FONT="System"][/FONT]

Hi,

I am new to ubuntu and have installed 6.10 on my 2xAMD64 (dualcore) machine with an MSI K8N Diamond motherboard (2x Ethernet ports 1 Marvell Yukon and 1 Nvidia). I also have an MSI Dualnet Card, which offers both bluetooth and wifi 802.11g connectivity.

The system installed and recognised all the major components including the wireless card. The dualnet card actually works in the same way as having a usb bluetooth adapter and a PCI ralink 2500 chipset wireless card. (correct linux driver for 2500 chipset correctly loaded)

On boot wireless does not work, however by inputting commands in terminal in the following sequence i manage to get wifi connected.

Some background info and things i tried:
- My router is set to DHCP. (Range 192.168.2.100 - 110)
- I require setting DNS to 192.168.2.1 manually (will not work otherwise, same problem experienced in XP .... ut us probably related to my router/cable provider)
- wifi card is recognised as RA0 (unknown)
- iwconfig lists my card as wireless capable.
- if ra0 card is enabled in System -> Administration -> Networking and set to DHCP = no connectivity
- DHClient, ifup etc.. fail to assign IP to the card. I have read that this is an issue with some PCI cards in ubuntu 6.10 so i have no problem opting for static ip. (Static IP is set as 192.168.2.100 / suben 255.255.255.0 / gw 192.168.2.1) = no connectivity. 
- in all the above cases
- "#iwlist scan" lists my router (wireless AP)
- iwconfig lists my card as wireless capable.
- If config shows no packets are received.



The only way i get associated to Network AP>

**Only way it worked**-  

in System -> Administration -> Networking  Ra0 checkbox is not enabled. However the second checkbox in the device settings is enabled. Static IP is set as 192.168.2.100 / suben 255.255.255.0 / gw 192.168.2.1

(NO CONNECTIVITY YET)

Then after setting
# ifconfig ra0 192.168.2.100 

# ifconfig up

# route add default gw 192.168.2.1

I am connected to my AP and have internet connectivity !


I would like to know... 

1. Is there a way of avoiding this process (manual setting from terminal) each time i boot
2. Is there a way of getting these settings from the GUI.. - 
System -> Administration -> Networking 


Please do get back to me if you need more clarification....

---

### Post by FrodoB on 2006-11-29
Please publish the output of whichever is applicable please:
 
lspci 
 
lsusb

---

