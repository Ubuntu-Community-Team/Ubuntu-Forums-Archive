---
title: "HP Pavilion Wireless"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by wiseguy1515 on 2007-10-28
Hello,
I have an HP Pavilion dv8000. My wireless is not working very well at all-- it takes a really long time to connect (if it connects at all) in strong signal areas, and if it does connect it works very, very slowly. Basically even if it does connect I can't effectively use it. Any suggestions?
Thanks!

---

### Post by Lambert on 2007-10-28
If this is an internal wireless device, run the following command.

```

sudo lshw -C network
[code]

Also post out put of 

[code]
sudo iwconfig

```

---

### Post by wiseguy1515 on 2007-10-28
I ran the code but it's still being very very slow... Here's the output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PerunaNet"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:0B:86:A4:5E:10   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr: off   Fragment thr: off
          Encryption key:A2EB-3A17-1DFB-5825-8BC4-AB34-AE10-27A9-DCC5-0719-8017-3B3A-F183-0FFD-FC2E-8C09   Security mode: open
          Link Quality=56/100  Signal level=-53 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:3787  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Lambert on 2007-10-29
> **wiseguy1515 said:**
> I ran the code but it's still being very very slow... Here's the output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PerunaNet"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:0B:86:A4:5E:10   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr: off   Fragment thr: off
          Encryption key:A2EB-3A17-1DFB-5825-8BC4-AB34-AE10-27A9-DCC5-0719-8017-3B3A-F183-0FFD-FC2E-8C09   Security mode: open
          Link Quality=56/100  Signal level=-53 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:3787  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This looks like one problem.

> 
Rx invalid crypt:3787


it looks like a lot of your data can't be decrypted and the data is being dropped and retransmitted.

What driver are you using and encryption method?

---

### Post by knave on 2007-10-29
eth1      IEEE 802.11b/g  ESSID:"39ellice"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1B:2F:58:A3:3C   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:##########  Security mode:open
          Link Quality=40/100  Signal level=-70 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Hi I just thought I'd add that I'm having the same symptoms with my dv1000.  Feisty was perfect... 

By the way I added the hashes in the output... Never know if my neighbours are on here hehe!

---

### Post by Selcal on 2007-10-29
i had a connection problem with my wireless as well.  I had to stop all the encryption stuff ie wpa,wep, etc.  It works well with the MAC address lock-out feature that i have on my netgear router.  I only accept the MAC of my linux laptop.

---

### Post by wiseguy1515 on 2007-10-29
I'm pretty new to Ubunutu... how do I find out what driver I'm using? I just know that I installed something that Ubuntu recommended at the very beginning and that made my wireless at least see available networks.

---

