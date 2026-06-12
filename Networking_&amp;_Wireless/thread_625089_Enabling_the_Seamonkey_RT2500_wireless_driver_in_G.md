---
title: "Enabling the Seamonkey RT2500 wireless driver in Gutsy"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by mandyfester on 2007-11-27
Hello

I am another unhappy user with trying to get a reliable connection with the  crappy rt2x00pci driver. I am using a Hercules PCI wireless card using the Ralink chipset. 

I have just installed Gutsy after using Feisty quite successfully. 

My first problem was that the Network Manager was not connecting automatically to my home wireless network. I fixed this by removing it and installing the very good WICD. 
 
My remaining problem is getting the wireless connection more stable. Currently it is disconnecting randomly and crashes completely when I log in to my computer through another laptop using vncviewer.

I downloaded the latest rt2500 driver from seamonkey, compiled it and have got it loading successfully every time Gutsy reboots.  
 
The problem is that the unstable rt2x00pci and rt2x00lib drivers are still loading even though I added them to the blacklist

/etc/modprobe.d/blacklist
blacklist rt2x00pci
blacklist rt2x00lib

Everytime I restart Gutsy issuing the following command gives me the following result.

house@lounge:~$ sudo lsmod | grep rt2
rt2500                206312  0 
rt2x00pci              13184  1 rt61pci
rt2x00lib              21760  2 rt61pci,rt2x00pci
rfkill                  9616  1 rt2x00lib
mac80211              196104  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
input_polldev           6672  1 rt2x00lib
crc_itu_t               3456  1 rt2x00lib

So my question is how can I disable the rt2x00pci, rt2x00lib, rt61pci drivers so that I can start using the seamonkey rt2500 driver?

Thanks in advance

Andy

---

### Post by kevdog on 2007-11-27
Did you add the rt2500 driver to the /etc/modules file??  I'm not certain why the modules in the blacklist are still loading.

---

### Post by mandyfester on 2007-11-28
Yes I the rt2500 driver is written in the /etc/modules file

---

### Post by mandyfester on 2007-11-29
Hello

Since other Gutsy kernel modules are dependent on the crappy rt2x00pci modules they might be loading it even though it has been blacklisted. Do you recommend that I add them also to the blacklist?

> blacklist rt2x00pci
blacklist rt2x00lib 
blacklist rfkill
blacklist mac80211
blacklist input_polldev
blacklist crc_itu_t

Will I still be able to boot Gutsy with all these modules blacklisted?

Thanks

Andy

---

