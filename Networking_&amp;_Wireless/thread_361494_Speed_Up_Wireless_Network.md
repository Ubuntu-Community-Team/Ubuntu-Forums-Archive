---
title: "Speed Up Wireless Network"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by signature16 on 2007-02-14
I am trying to copy a few files from my Windows external HD to my Ubuntu laptop's desktop. 

I installed the proper Samba stuff and everything is working find except for the speed.  When I try to copy an 800mb file it takes like 45 minutes.

I am using a Wireless PCMCIA card

What can I do to speed up my network card? It should be transferring faster than this.  



LSPCI says this about my wireless card:

```

Ethernet Controller:  Marvell Technology Group Ltd.  88w8335 [Libertas] 80 2.11b/g Wireless (rev 03)

```

---

### Post by bnuytten on 2007-02-15
The output of iwconfig could be helpfull here.

---

### Post by signature16 on 2007-02-15
Here it is:
> brenden@brenden-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:BD:BE:83
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=5/153  Noise level=112/153
          Rx invalid nwid:0  Rx invalid crypt:3371  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

sit0      no wireless extensions.


---

### Post by bnuytten on 2007-02-15
Since you have 801.11b, i.e. 11Mb/s or 1.375 MB/s. Which means - in theory - it would take about 10 minutes to transfer the file. In practice, it will probably take 13-14 minutes to transfer the file due to the design of the wifi protocol.

A possible reason why it takes three times longer may be the high noise level of 112/153 and a low signal level. Position yourself at a meeting with tens of people, you have to talk to the person on the other side of the table but you can not move. Everyone around you is shouting (i.e creating noise) and the person who is talking to you is talking very silent (signal level). Two things you can do: eliminate the noise or bring the sender/receiver closer together.

The invalid crypt packet count makes me suspect there are a lot of errors in the packets received due to the low signal level and high noise. Using encryption will lower the troughput slightly.

---

