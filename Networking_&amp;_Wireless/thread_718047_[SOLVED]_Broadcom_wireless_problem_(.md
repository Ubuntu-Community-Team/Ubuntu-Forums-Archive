---
title: "[SOLVED] Broadcom wireless problem :("
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Aetheric on 2008-03-07
I've got a Broadcom 4301 wireless card in my Compaq Presario R3000, and it's literally breaking my heart trying to get it working with Xubuntu. I think I've tried just about everything on the forum - I've been at this for weeks, working on firmware or ndiswrapper and nothing seems to get it to work. The best I've got at the moment is the firmware enabled and the card switched on, and it seems to detect my wireless network, but I can't connect to it.

iwconfig gives:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETGEAR"  Nickname:"Broadcom 4301"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig eth1 gives:

eth1      Link encap:Ethernet  HWaddr 00:90:4B:61:81:A3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2283 errors:0 dropped:780 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97527 (95.2 KB)  TX bytes:20184780 (19.2 MB)
          Interrupt:11 Base address:0xc000 

sudo iwlist scanning gives:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:3A:F8:9E
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-50 dBm  Noise level=-47 dBm
                    Extra: Last beacon: 4ms ago

I'm getting desperate. A thousand internets to whoever can help me solve this - it's the only thing I can't get working on my old laptop, when my new Acer 9303 worked out of the box with Ubuntu. Also, I only use Linux at the moment, but when I had XP the wireless was alright most of the time.

Any help is most appreciated.

---

### Post by ratvomit on 2008-03-07
Hi - not sure how much help this is going to be, but here goes - 

I have a GatewayMX6453, which also has a broadcom wifi card.  *However,* my similar problem was in Feisty, not Gutsy.   Broadcom wireless functionality seems to be a common issue with Ubuntu.

I'm not sure if you are familiar with ndiswrapper, but that is what got it going for me.  More info here: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-0175516fa66edf5e205f179c0fddd719c0719dc7](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-0175516fa66edf5e205f179c0fddd719c0719dc7)

Not sure if you've come across it already, but that link should have most of the information you need.  It basically involves unpacking the .inf (driver) file from the .exe file, and making it function in Linux.  Once it is working, your card should show as wlan0 instead of eth0.  

Hope that helps you out some, I remember how much of a hairpuller it turned out to be for me - Cheers!

---

### Post by Aetheric on 2008-03-08
Didn't help and now my card doesn't detect anything at all. :'(

Gonna try it again, I might have done something wrong.

---

### Post by uberlube on 2008-03-08
Try the howto in my sig. hope it helps :)

---

### Post by Aetheric on 2008-03-08
Doesn't work.

Got ndiswrapper installed, and the driver is showing up as normal:

ndiswrapper -l

bcmwl5 : driver installed
device (14E4:4301) present (alternate driver: bcm43xx)

But my wireless card isn't showing up in iwconfig or ifconfig. I really don't know what else to do. I can't figure out where I'm getting it wrong.

If someone can tell me ANY linux distro that works with this wireless card, I'll go download it immediately.

{edit} in the meantime, I'm back to square 1. Uninstalled ndiswrapper, enabled the bcm43xx firmware, and rebooted - card recognised and switched on, and it can detect my wireless network, but it will not connect. At this stage I'm wondering if I have some other weird network problem with IP addresses or something.

---

### Post by rustybronco on 2008-03-08
reading material [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Aetheric on 2008-03-09
Hasn't helped, once again, although it does kinda seem to me that it's not the driver, it's something else equally weird.

I think the wireless connection isn't getting an IP address from the router. Why, I have no idea.

---

### Post by uberlube on 2008-03-09
I have had a the same problem when I was using XFCE. I believe that the issue is that your wireless is getting help up in the keyring manager. I dont know how to fix this unfortunately.

---

### Post by Aetheric on 2008-03-09
Time to get another distro then... Gonna try Linspire and Mepis for now.

---

### Post by Aetheric on 2008-03-10
SOLVED!

I had another go with ndiswrapper, and followed this HowTo here:

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

It worked perfectly on my laptop! Once again, it's a Compaq Presario R3000 with a Broadcom 4303 wireless adapter in it, running Xubuntu 7.10. It looks like the instructions for the 4306 chipset works just as well with this one. :)

The problem seemed to be that my laptop has an Athlon 64bit processor, which needed the 64bit drivers listed in this HowTo. Word to the wise if you've got a Broadcom and the drivers don't seem to work - check which drivers you need!

Thanks to everyone who posted here and gave me the tips to get this piece of crap wireless connection going. It all got me closer to getting the solution.

---

