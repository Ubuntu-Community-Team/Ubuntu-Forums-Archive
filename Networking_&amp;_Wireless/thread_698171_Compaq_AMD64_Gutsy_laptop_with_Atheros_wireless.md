---
title: "Compaq AMD64 Gutsy laptop with Atheros wireless"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by SparcMan on 2008-02-16
I've poured hours into this issue with no luck yet.
I am using ndiswrapper with the 64bit XP driver for the integrated Atheros AR5006EG wireless NIC.
Presently, I can get a wlan0 device and show that I'm connected in iwconfig (ESSID is set and I show the signal strength), but no matter what, I get no network connection. I've tried everything I could think of including reload the ndiswrapper module and turn off WEP on the router. I've also tried ifconfig wlan0 down; ifconfig wlan0 up I'll show you what I have:
```
:~# uname -a
Linux DTN-Lappy 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux


```
```
:~# lspci | grep Wireless
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


```
```
:~# ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


```
```
:~# lsmod | grep ath


```
(Proof that I have the madwifi module unloaded - I've already tried that route too with no success)
```
:~# lsmod | grep ndiswrapper
ndiswrapper           233632  0 
usbcore               161584  4 ndiswrapper,ohci_hcd,ehci_hcd


```
```
:~# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"my_wireless"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:09:5B:4E:C6:8C   
          Bit Rate=54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:176390   Missed beacon:0


```
```
:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:50:B9:16  
          inet6 addr: fe80::21e:4cff:fe50:b916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38256 (37.3 KB)  TX bytes:468 (468.0 b)
          Interrupt:19 Memory:f6000000-f6010000 


```
```
:~# modinfo ndiswrapper 
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.45
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     F2ACCEB45C744303696E0F1
depends:        usbcore
vermagic:       2.6.22-14-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


```
(note that I am NOT using IPv6 so the IPv6 address above is garbage - the wireless router is an older Netgear that has no support for IPv6)
The router has an access list and this computer and its wireless MAC is entered on the access list.
The router also has an "Attached devices" list that only shows this computer if the physical link is connected to eth0
It seems like the driver is running and connected to the wireless NIC, but it's not properly connected to networking.

---

### Post by rustybronco on 2008-02-16
> **SparcMan said:**
> I've poured hours into this issue with no luck yet.
I am using ndiswrapper with the 64bit **XP driver** for the integrated Atheros AR5006EG wireless NIC.
**net5211** : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

wlan0     IEEE 802.11g  ESSID:"my_wireless"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:09:5B:4E:C6:8C   
          Bit Rate=54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          **Tx excessive retries:2  Invalid misc:176390**   Missed beacon:0

It seems like the driver is running and connected to the wireless NIC, but it's not properly connected to networking.I would seeem the wrong driver is used, so possibly try the net5416 drivers?
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)
> The name of the driver of the new version is net5416 (instead of net5211 that is mentioned on other instructions)
You only need the .inf file that is contained on the ZIP (although I also copied the .sys file, just in case)


---

### Post by lswest on 2008-02-16
also, you can see if you can request an IP from your dhcp server (aka router) with ```
sudo dhclient wlan0
```  might give you a bit more information^^

---

### Post by SparcMan on 2008-02-17
> **rustybronco said:**
> I would seeem the wrong driver is used, so possibly try the net5416 drivers?
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

The links in that post may have once led to the net5416 driver, but they now point back to the net5211 driver which doesn't appear to be working for me. Does anyone have an updated link?

Also, thanks for the tip on the sudo dhclient wlan0 command. I'll try later, but I don't think thats where the problem is.

---

### Post by rustybronco on 2008-02-18
[http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1)
[http://ubuntuforums.org/showpost.php?p=4279390&postcount=303](http://ubuntuforums.org/showpost.php?p=4279390&postcount=303)
xp32-6.0.3.85.zip

look at the  the correct chipset (you probably want to i.d. your chipset from the numbers on it)
***note some ar5006eg are incorrectly identified by lspci***

more helpful threads...
[http://ubuntuforums.org/showpost.php?p=4318876&postcount=315](http://ubuntuforums.org/showpost.php?p=4318876&postcount=315)

original thread [http://ubuntuforums.org/showthread.php?p=4279390#post4279390](http://ubuntuforums.org/showthread.php?p=4279390#post4279390)

---

### Post by SparcMan on 2008-02-19
I have AIDA32 on an XP live boot CD I created which should report exactly what the chipset is. I'll let you know if I have a different chipset and need to change the driver. I really want this to work I don't accept defeat easily. I also want to get my wife interested in using Linux as this laptop is going to be the last and only computer we have running Vista or any newer M$ operating system.

---

### Post by SparcMan on 2008-02-22
Actually, booting to the pre-installed Vista on the same system reveals the wireless chipset is the AR5007 which has no XP 64-bit drivers and no 64bit support in MadWiFi. There are also no XP 64-bit drivers for net5416 which was also suggested. I tried putting in the Vista driver, but that clearly wasn't sucessfull. It looks like I will not have any wifi support for this until MadWiFi adds 64bit support for this chipset (sure, I could plug in a USB wifi adapter that is suppoted, but this IS still a dual boot system and it's still free to just reboot and go to Windows).

---

### Post by SparcMan on 2008-02-22
For future reference the exact model of laptop is Compaq Presario F756NR

---

### Post by johndoe32102002 on 2008-03-18
Having same problem with the Compaq F756NR and Ubuntu.

---

### Post by Huahua on 2008-03-28
Hey i wonder if someone has network drivers for a Compaq Presario F756NR becouse i cant connect to any network or internet. rly would like some1 to send me it ;)

---

