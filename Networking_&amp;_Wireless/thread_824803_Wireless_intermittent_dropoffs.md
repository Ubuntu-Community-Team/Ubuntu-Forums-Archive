---
title: "Wireless intermittent dropoffs"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by pstasho on 2008-06-10
Hello all, 

I'm running Gutsy on a Dell Latitude D430 with a Broadcom NIC and I'm using the default network manager.  I keep having a seriously annoying situation with the NIC when I'm on wireless at home.  I can and will connect but it takes quite a while.  When I do connect, the reception will intermittently drop off or disconnect from my network all together.  Then, it will sometimes connect to one of the neighboring unsecured wireless networks but there seems to be no issues with reception on the neighboring networks.  This is a dual boot lt so to troubleshoot I've tried to connect to my network on the windows side of things and I have no issues so I think it has to be a config issue with Ubuntu.  

Can someone please help me troubleshoot/fix this issue?

---

### Post by PRMan on 2008-06-10
If you can get the chipset (sudo iwconfig) of the Broadcom and also what brand your wireless switch is, that would help.

I had a Netgear wireless switch and it just dropped off intermittently.  I switched to a Linksys and I haven't had any problems since.

---

### Post by pstasho on 2008-06-12
eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm using a 2wire gateway.  It's what I have to use for my net connection from AT&T because my UVerse connection relies on it.

---

### Post by pstasho on 2008-06-16
Ping, anyone?

---

