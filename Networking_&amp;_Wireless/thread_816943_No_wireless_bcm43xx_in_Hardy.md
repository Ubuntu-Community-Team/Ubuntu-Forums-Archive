---
title: "No wireless bcm43xx in Hardy"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by captgadget on 2008-06-03
I'm having a terrible time getting the wireless functioning in Hardy. I've followed so many posts and have tried so many suggestions that as you can see in the screen shots I've got double entries all over the place. Would these be hindering me? Also when I go to System> administration>Network>Wireless connections I deleted some of the settings in Hosts. Could that also be some of my problem.





Thanks to all those who make this such a great forum.

---

### Post by superprash2003 on 2008-06-03
could you post your iwconfig output

---

### Post by captgadget on 2008-06-03
captgadget@captgadget-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"private network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:8E:CA:C4   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by captgadget on 2008-06-03
If nothing else can someone tell me how to remove all the above in the screen shots so I can start all over?

---

### Post by cdtech on 2008-06-03
I just can't believe all the problems we're having with this issue. I had a perfect setup with Gutsy and now I'm pulling my hair out trying to config Hardy. What was changed and isn't the idea of an upgrade to  improve?

I finally have my wifi up but far from correct. I can browse the internet for just a brief time and then I need to reset the modules to get it to work again.

I found this among other suggestions somewhere so I'm not taking credit for this and maybe you'll have better luck than I have.
----------------------------------------------------------------------

I used the following steps to enable my Broadcom Wireless BCM4312 (rev 02).

Step 1 (run in terminal)

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

For Step 2, You can check your Broadcom wireless version with this command in terminal : "lspci | grep Broadcom\ Corporation",if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/Wi...f971ca757b2851](https://help.ubuntu.com/community/Wi...f971ca757b2851)


Step 2 (run in terminal)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
cabextract sp34152.exe

Step 3 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....

---

### Post by Ayuthia on 2008-06-03
> **captgadget said:**
> I'm having a terrible time getting the wireless functioning in Hardy. I've followed so many posts and have tried so many suggestions that as you can see in the screen shots I've got double entries all over the place. Would these be hindering me? Also when I go to System> administration>Network>Wireless connections I deleted some of the settings in Hosts. Could that also be some of my problem.





Thanks to all those who make this such a great forum.

Those files are for the depreciated bcm43xx driver.  The new driver is b43.  However, some cards did work with the depreciated driver.  You can try to see if it works by trying:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```
I am guessing that the b43 driver is causing conflicts with bcm43xx.  By default, bcm43xx is blacklisted in /etc/modprobe.d/blacklist.  

The information that you posted looks fine.  If you don't want to use them, you can just blacklist the module (most likely is already blacklisted) otherwise they can be used for the bcm43xx module.

Can you also post your lshw -C network?  It is possible that you can use the new drivers also.  I have a 4311 rev 01 card and I am able to use the bcm43xx, b43, and ndiswrapper options, but not all cards are able to do this.

---

### Post by vexingmodstwo on 2008-06-03
Hello,

I followed a few of the how to's regarding these stupid Broadcom wireless cards and once I finally had the drivers correctly and wlan0 showed up correctly, it still wouldn't work.

I don't know what the problem is exactly but for some setups the card just refuses to let itself get the DHCP update.

I wound up replacing Network Manager with WICD, but that didn't work.  I then replaced WICD with wifiradar and manually configured the connection and that finally did the trick.

You might want to try installing wifiradar.

---

### Post by captgadget on 2008-06-03
Sorry folks, I had to head off for work so I won't be able to play around until tonight. Let's all hang in there and hopefully we can get these units running. At least I have wired for the time being. Proabalby shouldn't even worry about it, but you know how we geeks are.

Everyone have a great day!!!!!!!!!!!!!!!!

---

### Post by captgadget on 2008-06-03
*-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 03
       serial: 00:0c:41:63:c9:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-17-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:1d:c1:08
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.2.206 latency=64 mingnt=255 module=e1000 multicast=yes

---

### Post by Ayuthia on 2008-06-03
> **captgadget said:**
> *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 03
       serial: 00:0c:41:63:c9:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-17-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:1d:c1:08
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.2.206 latency=64 mingnt=255 module=e1000 multicast=yes

It looks like it is using the bcm43xx driver.  Are you able to see any wireless networks from the Terminal?  I think that Network Manager cannot see the wireless networks through bcm43xx.
```
sudo iwlist scan
```

---

### Post by captgadget on 2008-06-03
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Now, if I copy and paste these two lines from you it will run until I shut down. It will not come back on it's own.

---

### Post by captgadget on 2008-06-03
Network manager sees the wireless connection. In fact it's running right now, but when I shut it down it'll be gone when I bring the computer up again.

---

### Post by Ayuthia on 2008-06-03
> **captgadget said:**
> Network manager sees the wireless connection. In fact it's running right now, but when I shut it down it'll be gone when I bring the computer up again.

If that is the case, make sure that bcm43xx is not blacklisted in /etc/modprobe.d/blacklist and that b43 is blacklisted.  You might even take the extra step and add bcm43xx to /etc/modules.

---

### Post by Chas_E_Erath on 2008-06-04
My Broadcom card was working until this Hardy upgrade.  I seem to have it working now, but I've flailed away at it so much now that I don't know what I've done or undone anymore.  Surprisingly I think my config files are mostly untouched.

However, I do know that I upgraded the bm43-fwcutter(?) package, and I know that I've disabled the avahi daemon.  I also know that I commented out all of the previously pertinent lines in my rc.local file, and that I added 2 lines at the end.

My /etc/rc.local file now looks like this:

```


# wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_psk.conf  &
# ifconfig eth0 down
# ifconfig eth1 down
# dhclient -r eth1
# iwconfig eth1 essid "MYESSID" 
# iwconfig eth1 mode Managed
# ifconfig eth1 up
# dhclient eth1
/etc/init.d/networking stop
/etc/init.d/networking start
#
#exit 0

```

Its odd that it this is what it takes to get the card going, because I know that /etc/init.d/networking is getting called before rc.local is run.

Hope that helps someone.

Chas.E.Erath

---

### Post by captgadget on 2008-06-04
I did the software updates this morning. I had the green light. I used Network Manager to edit wirless and now I lost the green light on the wireless card. Ayuthia, that was before I made your suggested changes.

---

### Post by captgadget on 2008-06-04
OK, I did a complete shut down and restarted. Now I have the green light but still not able to acess wireless network.

---

### Post by captgadget on 2008-06-04
Here's what I have now:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:8E:CA:C4
                    ESSID:"private network"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=86/100  Signal level=-43 dBm  Noise level=-62 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000554f8e924a

---

### Post by Ayuthia on 2008-06-04
> **captgadget said:**
> Here's what I have now:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:8E:CA:C4
                    ESSID:"private network"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=86/100  Signal level=-43 dBm  Noise level=-62 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000554f8e924a

If you remove the encryption, does it work?

---

### Post by captgadget on 2008-06-04
You mean remove the password at the router?

---

### Post by captgadget on 2008-06-04
When I go to Network Tools, Select Wlan0, it gives me a choice to configure. Then when I click configure it tells me:The interface does not exist. But as you can see in the  post #18 it is there!

---

