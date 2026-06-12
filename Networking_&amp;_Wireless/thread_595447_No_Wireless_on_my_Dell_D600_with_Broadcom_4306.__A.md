---
title: "No Wireless on my Dell D600 with Broadcom 4306.  Anyone Advice?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by bzak on 2007-10-28
I just can't seem to get this to work after 3 days.  Fresh install of Gutsy...Anyone seen a "How To" that works?

---

### Post by gargouille on 2007-10-29
I was able to get the wireless working with my D600, although it was with the Broadcom 4309.  Immediately after installation of Gutsy there was a notification from the Restricted Drivers Manager (System > Administration > Restricted Drivers Manager).  I enabled the "Firmware for Broadcom 43xx chipset family, and have not had a problem since.

After enabling the driver left click on the network connection utility on the top tool bar (similar to Cingular ads) and then configure the connection.

---

### Post by bzak on 2007-10-29
I have tried from a fresh install twice.  Still no luck.  I am running it with a Linksys BEFW11S4 v.2 Router.  I went to the network list and clicked 'Connect to Other Wireless Networks'.  Wen it asked for the name I typed 'linksys' which is what my XP labtop uses.  I am able to connect to the router through a cable though.

Here are some more relevant details:

lshw
           *-network:1
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 02
                serial: 00:90:4b:2f:c0:d1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by staticsage on 2007-10-29
This howto is stickied on this forum: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by bzak on 2007-10-29
Ok I tried installing the firmware and the ndiswrapper.  Neither worked.  In fact, I no longer even see the card.  Is anyone else experiencing problems with this card?  Any other suggestions?

---

### Post by bzak on 2007-10-29
I reinstalled the ndiswrapper and now see the card again but still no wireless connection.  AN interesting thing happened on my XP labtop though.  It said that there was an IP conflict with another computer on the network.  I shut both down completely as well as the router and restarted only the router and Ubuntu labtop.  Still nothing.

---

### Post by gargouille on 2007-10-29
Perhaps these other posts can be of help:

[http://ubuntuforums.org/showthread.php?t=201902&highlight=4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=4306)

[http://ubuntuforums.org/showthread.php?t=340689&highlight=4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=4306)

---

### Post by kevdog on 2007-10-29
Look at the bottom of my tutuorial (connecting from the command line -- this is found in my signature) for a link by Jamie Jackson about 5 minute installation with broadcom cards.

Use ndiswrapper -- much more reliable that built-in driver.

---

### Post by tashmooclam on 2007-11-02
I was able to get wireless of a sort with the same equipment as you. Broadcom 4306.
I was prompted by Ubuntu to get the restricted driver. I am pretty sure that this driver is not part of Ubuntu, but must be downloaded.
Ubuntu 7.1 can get it in synaptic. The driver was called "bcm43xx-fwcutter." 
After a lot of variable wireless connections, I decided to switch from Network Manager (default in Ubuntu) and install a little app called "Wicd". 
This actually caused a slight improvement but still my connections will be from Okbs to 345kbs, and in between.
So, my point? Even if you get the driver and use either Network Manager or switch to Wicd, you may not get a good wireless connection. 
I don't know about the ndiswrapper, and I guess I should research that and give it a try.

---

### Post by bluedragon436 on 2007-11-02
I was able to get my D600's wireless to work seamlessly...as well as my D610...that only issue I have is some times it decides to fluctuate the signal without my computer having ever moved....but other than that I have had no issues on either laptop...

---

### Post by tashmooclam on 2007-11-03
Which method did you use go get the wireless to work, Ndiswrapper or bcm43xx-fcutter? 
I found that for $24 you can get a better intel wireless card.
By the way, Intel has linux drivers for their wireless cards on their website available for download.
I had wireless with bcm43xx-cutter that went from 0kbs-347kbs and everywhere in between.

---

