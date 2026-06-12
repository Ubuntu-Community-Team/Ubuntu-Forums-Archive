---
title: "compaq c700 wifi help! Almost there!"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by newuser0000 on 2008-11-17
So I followed the directions to install my wifi driver here:

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

everything worked, but I can't detect networks. the wireless networks button on the top of ubuntu is greyed, and wifiradar can't pick up any networks. I've even manually entered my router's info, but it can't be detected. 

So, my driver is installed but i can't detect a network. I've included some info below. Any suggestions?

user@10110:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

user@10110:~$ uname -a
Linux 10110 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
user@10110:~$ cat /etc/issue
Ubuntu 8.10 \n \l

user@10110:~$ iwlist wlan0 scanning
wlan0     No scan results

user@10110:~$ lspci | grep Atheros
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

When I unload and load the driver, I get:

user@10110:~/Desktop/compat-wireless-2008-11-17$ sudo make unload
[sudo] password for user: 
user@10110:~/Desktop/compat-wireless-2008-11-17$ sudo make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully

---

### Post by busstation16 on 2008-11-18
I have no idea what your issue is, but this worked for me:

[http://ubuntuforums.org/showthread.php?t=839061](http://ubuntuforums.org/showthread.php?t=839061)

---

### Post by kbar78 on 2008-12-22
I had the exact same problem on the same model of laptop after upgrading to 8.10.  Try pressing your wireless button just above your keyboard and holding it for a second or so.  This finally got the wireless networks to show up for me.  It's annoying because with Hardy, when I was using madwifi, the button didn't use to function at all and now that it does something the indicator light still doesn't change.


Hope this helps

---

