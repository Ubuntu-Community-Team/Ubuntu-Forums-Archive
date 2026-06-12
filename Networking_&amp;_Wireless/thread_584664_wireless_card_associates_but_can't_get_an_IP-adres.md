---
title: "wireless card associates but can't get an IP-adress"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by tapetersen on 2007-10-21
ok using either networkmanager or the commandline I can get the card to associate. iwconfig:

eth1      IEEE 802.11g  ESSID:"hemmarf"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:15:E9:1E:DA:4A   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:1532-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality=49/100  Signal level=-80 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:529  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0

(the x's are my own)
from what I see that is in order. The router is a D-link 624 if I remember correctly.
The card is a:      
description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:04:88:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
 
When I try dhclient it tries for a time and times out.

It works with the wired connection.
any help appreciated

---

### Post by tapetersen on 2007-10-21
ok other interresting bits it's Ubuntu 7.10-amd64

---

### Post by unki on 2007-10-21
I have the same problem you have, even the same Wireless card. If I set off the security in my routers (I have tested with 2 diffrent routers) it works too, but when i enable any kind of security it does not get ip...I also had the same problem with ubuntu feisty....please help!!:(
PD:64 bit OS too...

---

### Post by Hero of Time on 2007-10-21
Are you certain that the key is entered correctly? When the key is incorrect, you will associate with it but not connect with it. Let's say you use a different, non existing SSID like 'nobodyhome' and use iwconfig, you will see it has associated with 'nobodyhome' SSID. Have you tried connecting with wpa_supplicant?

---

### Post by tapetersen on 2007-10-21
Ok feeling stupid. wrong key. I didn't think you could associate without the correct key. Apparently you can. should have seen that from all the "Rx invalid crypt:529" solved for me. just hoping it's the same for you unki.

---

### Post by unki on 2007-10-21
I have entered the key correctly, the only thing that can be wrong is the key type or the authentification, but the fact is  that i have tested changing the key (and it's tipe, i have proved wep hex 64bit, wep hex 128 bit and also wpa...), about the authentification, i have tested trying  with both options and it doesnt work....
Also, sometimes it does not connect, it asks for the key repeatedly, but when i try to connect with the wifiradar it says that it is connected (but it has no ip)
Well, when i trie to connect with the gnome netmanager it doesnt connect even changing the key....it does only connect withoith key...(when i dissable it from the router)

---

