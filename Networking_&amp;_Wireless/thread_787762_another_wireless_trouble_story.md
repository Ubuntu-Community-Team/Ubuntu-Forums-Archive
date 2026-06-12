---
title: "another wireless trouble story"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by rem on 2008-05-09
Hello,

Yesterday I did an upgrade to Hardy and my wireless ceased working. It was working fine under Gutsy and now I'm without an Internet connection on this particular machine.

I searched over this forum and tried few of the tricks but non of them worked. I had a driver installed when on Gutsy, removed it, installed it back on, restarted the network, nothing... It seems that my card is recognized but still no go. Here are the outputs of 
```

lspci -nn
lshw -C network
```

which seem to be the commands to start with.

```
lspci -nn
==========================================
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGC) [8086:1132] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:0a.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)






lshw -C network
===================================================
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 10
       serial: 00:0a:cd:10:cd:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=66 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=66 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1e:8c:02:2c:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



```

I'd appreciate if you could help me fix this or point me to a helpful resource.

Thank you!

---

### Post by kwacka on 2008-05-09
Does this help?```
sudo ifup eth1
```

---

### Post by rem on 2008-05-09
no, sorry, it says that the eth1 is already configured ...

---

### Post by Ayuthia on 2008-05-09
Your lshw -C network is showing signs that firmware is missing.  The native drivers for Broadcom have changed from bcm43xx to b43.  In order to get it to work, you will need to install b43-fwcutter:
```
sudo apt-get install b43-fwcutter
```and make sure that bcm43xx is blacklisted in /etc/modprobe.d/blacklist.

If you do not have a working connection, here is a link that will tell you where you can get the files you need to get it installed:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by rem on 2008-05-09
You are perfectly right! I did had the bcm43xx driver installed and removed it and installed the b43 but in my own way. I didn't blacklisted the old one ... I will follow the thread you pointed me to and get back here with the results.

Thanks a lot!

---

### Post by rem on 2008-05-09
So:

I made sure the old driver is blacklisted and it was, i installed the new driver b43-fwcutter, followed the steps from the above tutorial exactly and the output of 

```
sudo ifconfig wlan0 up
```


returns:

```
wlan0: ERROR while getting interface flags: No such device
```

and still not working ...

Any ideas?

---

### Post by Ayuthia on 2008-05-09
> **rem said:**
> So:

I made sure the old driver is blacklisted and it was, i installed the new driver b43-fwcutter, followed the steps from the above tutorial exactly and the output of 

```
sudo ifconfig wlan0 up
```


returns:

```
wlan0: ERROR while getting interface flags: No such device
```

and still not working ...

Any ideas?

I probably should make a clarification on this.  Yours is acutually eth1.  Why don't you try:
```
sudo ifconfig eth1 up
```
If that doesn't work, please post your lshw -C network information.

---

### Post by rem on 2008-05-09
Unfortunately it is not working... 
Here is the lshw -C network info and thanks a lot for taking the time to help .


```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 10
       serial: 00:0a:cd:10:cd:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=66 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=66 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1e:8c:02:2c:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by Ayuthia on 2008-05-09
It looks like the firmware is there.  What information do you see from ifconfig, iwconfig, and sudo iwlist scan?  Are you using encryption?  If so, it might help to turn it off just to see if we can connect.

---

### Post by rem on 2008-05-09
> It looks like the firmware is there. What information do you see from ifconfig, iwconfig, and sudo iwlist scan? Are you using encryption? If so, it might help to turn it off just to see if we can connect.

Yes, indeed I'm using encryption . Next, I will turn it off and see what's happening.

```
ifconfig
==============================================================
eth0      Link encap:Ethernet  HWaddr 00:0a:cd:10:cd:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:02:2c:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:1e:8c:02:2c:71  
          inet addr:169.254.4.34  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67128 (65.5 KB)  TX bytes:67128 (65.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-02-2C-71-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






iwconfig
==============================================================

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"underskin"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sudo iwlist scan
================================================================
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:7E:BC:9B:D1
                    ESSID:"underskin"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/100  Signal level=-51 dBm  Noise level=-57 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000036c701118a



```

---

### Post by rem on 2008-05-09
the encryption is off but still no go... i don't understand why is so hard to make this work?! beats me ...

is there a way i can find out if my wireless card is supported?

thank you.

---

### Post by Ayuthia on 2008-05-09
I am pretty sure that it is, but the 4318 has been somewhat troublesome.  [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) is the place to go to confirm.

What happened with sudo iwlist scan?  Any results?

---

### Post by rem on 2008-05-09
> **Ayuthia said:**
> What happened with sudo iwlist scan?  Any results?

Yes, already posted that on the 1st page, last post.

Thanks.

---

### Post by Ayuthia on 2008-05-09
Ok.  You can see an access point.  You might try changing to another channel on your router (less than 11) and see if you can connect without encryption manually:
```
sudo iwconfig eth1 essid underskin
sudo dhclient eth1
```

It looks like it can see things but dhclient is not issuing anything out.  Could just be interference.

---

### Post by rem on 2008-05-12
I tried to connect manually without encryption but it is not working. I didn't changed the channel though because I don't know how to do that ... Are there other alternatives I could try (NDISwrapper)? Could you recommend another card which is know as working with Hardy? Downgrade back to Gutsy? 

Thanks a lot!

---

### Post by rem on 2008-05-12
> **rem said:**
> I didn't changed the channel though because I don't know how to do that ... 

I finally managed to change the channel as well. So: the encryption is off, the channel is switched to 8 and manually connection still not working. The final output is:

```
No DHCPOFFERS received.
No Working leases in persistent database - sleeping
```

---

### Post by rem on 2008-05-12
I also went through the b43/b43legacy Troubleshooting Tips post [http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692) and everything is ok...

---

### Post by martin15s on 2008-05-12
try the Edimax wireless cards - I use the EW-7108PCG pcmcmia card - all of their cards are straight from the box compatible with 8.04 -

---

### Post by Ayuthia on 2008-05-12
> **rem said:**
> I also went through the b43/b43legacy Troubleshooting Tips post [http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692) and everything is ok...
Can you attach your dmesg?  I am curious if there are any error messages coming up for it.

---

### Post by rem on 2008-05-12
> **Ayuthia said:**
> Can you attach your dmesg?  I am curious if there are any error messages coming up for it.

sure, here it is (attached):

---

### Post by rem on 2008-05-12
> **martin15s said:**
> try the Edimax wireless cards - I use the EW-7108PCG pcmcmia card - all of their cards are straight from the box compatible with 8.04 -

Are you sure about this? I know this isn't going to cost me the world but I don't want to pay for a new card then struggle again for days to make the wireless working... Thanks for the suggestion!

---

### Post by Ayuthia on 2008-05-12
> **rem said:**
> Are you sure about this? I know this isn't going to cost me the world but I don't want to pay for a new card then struggle again for days to make the wireless working... Thanks for the suggestion!

Before you go that route, you might try to install NDISwrapper.  Here is a link that works well for most:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I am currently checking to see if the 4318 rev 02 cards are working with b43.  I have not found too many people that have been successful with it.

EDIT:
I looked at dmesg and did not say anything strange about it.

---

### Post by rem on 2008-05-12
Thanks a lot, I really appreciate you did your best to help! I will come back and tell about the ndiswrapper adventure ...

---

### Post by rem on 2008-05-12
> Before you go that route, you might try to install NDISwrapper. Here is a link that works well for most:
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

Step 3 returns this error (with both 2a or 2c steps):

```

sudo ndiswrapper -i bcmlw5.inf

Couldn't open bcmlw5.inf. No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

```

And I am sure I was inside the folder containing the bcml5.inf file

Any thoughts?

---

### Post by Ayuthia on 2008-05-12
> **rem said:**
> Step 3 returns this error (with both 2a or 2c steps):

```

sudo ndiswrapper -i bcml5.inf

Couldn't open bcml5.inf. No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

```

And I am sure I was inside the folder containing the bcml5.inf file

Any thoughts?

You might try bcmwl5.inf.  I think you left out the w.  Hope that helps.

---

### Post by rem on 2008-05-12
> You might try bcmwl5.inf. I think you left out the w. Hope that helps. 

yes, indeed you're right... i am a bit tired and even i looked and looked for an error, i couldn't find it.

i did the rest of the how-to and it finally worked. hopefully it's going to be there after reboot as well. if not, i guess i'm going to be dealing with that part some other time. i am happy to know it is working!

THANKS A LOT!

---

