---
title: "Wireless not working on Compaq n610c with Cisco Aironet 340 card"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by oldtappan on 2005-11-12
Compaq n610c hardware that worked with Warty, Hoary as well as OpenSuse 10 doesn't work on Breezy.  My wireless PC Card is a Cisco Aironet 340.  

I'm trying to connect to a Belkin Wireless G Router that expects 64-bit wep encryption.  My WinXP boxes can connect to it perfectly, as did a prior installation of OpenSuse 10 on the same box.

I'm guessing if I disabled WEP, my wireless would work but I don't even want to consider that option.

Please help.

The results of the usual commands are below:
**iwconfig**
eth1      IEEE 802.11-DS  ESSID:"MyNet2"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:11:50:8B:4C:1A
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-97 dBm
          Rx invalid nwid:46591  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:221688   Missed beacon:0

**iwlist eth1 scanning**
eth1      Scan completed :
          Cell 01 - Address: 00:0D:3A:26:30:61
                    ESSID:"MyNet"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:30/100  Signal level=-80 dBm  Noise level=-96 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
          Cell 02 - Address: 00:11:50:8B:4C:1A
                    ESSID:"MyNet2"
                    Mode:Master
                    Frequency:2.467 GHz (Channel 12)
                    Quality:95/100  Signal level=-48 dBm  Noise level=-96 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s

**iwlist key**
lo        no encryption keys information.

eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: ****-****-** (40 bits)
                [2]: ****-****-** (40 bits)
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open

---

### Post by Lambert on 2005-11-12
> **iwconfig**
 eth1      IEEE 802.11-DS  ESSID:"MyNet2"
           Mode:Managed  Frequency:2.442 GHz  **Access Point: 00:11:50:8B:4C:1A**
**           Bit Rate:11 Mb/s**   Tx-Power=15 dBm   Sensitivity=0/65535

According to this you are connected to your router at 11Mb/s.

Trying pinging the router and your other pcs. then an external site.

---

### Post by oldtappan on 2005-11-13
Despite what **iwconfig **says, **ifconfig **shows that eth1 doesn't have an IP address.  So I can't ping anything...

---

### Post by Lambert on 2005-11-13
you're connected to the router. The problem is you're not being assigned an ip address. Are you using dhcp or static and did you double check these?

You should be able to ping the router but nothing else.

---

### Post by oldtappan on 2005-11-13
I'm using DHCP and I'm not getting an address.  So there's no way I can ping the router.  

I tried assigning a static IP and my pings don't work.  

My router expects a 64 bit hex WEP key.  How can I check whether the value I enter is being interpreted as 64 bit hex?

---

### Post by mips on 2005-11-13
Maybe disable WEP first and see if it works and then go on from there.

---

### Post by oldtappan on 2005-11-14
I disables WEP and it still wouldn't connect!  I tried to connect to another AP in my house and that didn't work either.

Does anyone know how I can specify the WEP key strength (40, 64 or 128 bit) using the command line tools?

---

### Post by 7echno7im on 2007-05-06
I am having the same issues.  The Cisco 340 and Ubuntu (or even Kubuntu i am using) is shoddy at best.  I use the knetworkmanager and it seems to take 3 or 4 reboots before i can connect to my access point.  On my T60 lenovo, no problems at all, never not once.  I think it is the 340 drivers for ubuntu and considering the sourceforge project for this driver hasn't been updated for 6 years, i don't see it getting any better unless cisco themselves release an official driver.  Your best bet is to go buy a cheap linksys pcmcia card, you can get one for about 10 bucks now-a-days.  I broke down and started using my 2wire.  Funnny, and enterprise card that supports all the authentication types won't work so hot with wep and I have to use the lowest in the line, 2wire,and works fine.

---

