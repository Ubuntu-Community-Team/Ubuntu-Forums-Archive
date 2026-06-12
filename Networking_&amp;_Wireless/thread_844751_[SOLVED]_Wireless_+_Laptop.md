---
title: "[SOLVED] Wireless + Laptop"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by RMD94 on 2008-06-29
Hello,

i am new to Ubuntu, could anyone tell me how to connect to the wireless network? I have Asus Eee PC and i am usinng Atheros 802.11 wireless LAN card. I have already enabled the LAN card in Hardware Drivers, I just don't know how to set-up the wireless network. I right clicked on (the two computers icon on the top right) and clicked edit wireless networks but when the ask me for entering the bssids i can't type anything in the box..... I even tried typing the following in the terminal: 

sudo lshw -C network and i get

pratibha@pratibha-laptop:~$ sudo lshw -C network
[sudo] password for pratibha: 
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:37:ef:97
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 duplex=full firmware=L2 ip=192.168.2.16 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:4e:fe:ff:50:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
pratibha@pratibha-laptop:~$ 

actually this is my my mom's laptop, right now i am using wired connection. could someone plz help me????

plz don't forget to mention how to set-up the wireless connection.......    :lolflag:

plz help me!!!! plz plz plz plz plz plz plz plz plz plz plz plz plz

---

### Post by pastalavista on 2008-06-29
Does the Eee have a physical switch on it to turn the wireless on/off? My Acer does and it confused me once to think the network was broken when actually the switch was just in the off position. Be sure it's turned on.

---

### Post by RMD94 on 2008-06-29
no it doesn't have any switch.... the only way i can turn on and off my wireless is by holding down the function key on the keybord (Fn) and F2..

-Thanks

---

### Post by RMD94 on 2008-06-30
what i am asking is: i want to set up my wireless network. e.g. in Windows we can search the available networks around and click the one u r looking for and add the WEP key...  How can i do that in Linux....


plz plz plz help me

---

### Post by pastalavista on 2008-06-30
maybe this link will help

[http://ubuntuforums.org/showthread.php?t=798485&highlight=eee+wireless](http://ubuntuforums.org/showthread.php?t=798485&highlight=eee+wireless)

I have found that with a little patience, when I have a problem, I can usually search the forum to find the solution and don't need to post my own request for help.

To configure the network just right-click the icon in the tray-panel and click "edit wireless networks". You'll need to know the encryption type and passkey. after you configure it, the "keyring manager" should remember it for you.

---

### Post by RMD94 on 2008-06-30
i know the name of the ssid and the WEP key.. but when i click on it they ask me for the name and when i enter the name they ask for something bssids and i cannot type anything over their....

---

