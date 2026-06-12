---
title: "Intel Wireless Pro 2200 BG on Acer Travelmate 4102"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by fngaserin on 2006-10-25
I just had Dapper Drake installed. Everything seems to work fine except the wireless connection. I've got the screen resolution to work after help from 915resolution. I get my lan card to work after disabling IPv6. The only thing I can't get to work is the wireless connection. I've installed acerhk but I don't seem to get the solution. I've been browsing the whole day and tried a number of solutions found on the Net but I can't still figure out. Please help. Please help. Please help. I think most of the documentations in the Internet expect people who already have decent knowledge about Linux basic. Well, I don't. :)  By the way, I know ipw2000 and acerhk is loaded by using lsmod.

---

### Post by Kevomiller on 2006-10-25
Hey, we have the same problem!

I use wireless internet too.

I hope somebody answers you so I can figure it out. lol.

---

### Post by fngaserin on 2006-10-25
Seems like IPW2200 itself works since I can get results from iwlist scan.

This is the result of the iwlist scan

lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:60:B3:F3:16:DC
                    ESSID:"Musashi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=94/100  Signal level=-33 dBm
                    Extra: Last beacon: 196ms ago

However this is the result after I run dhcpcd eth1. I check on the iwconfig for eth1:

iwconfig eth1

eth1      unassociated  ESSID:"Musashi"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is the result of the ifconfig eth1

ifconfig eth1

eth1      Link encap:Ethernet  HWaddr 00:12:F0:2C:FD:1A
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xc000 Memory:b010a000-b010afff

What's wrong?

---

### Post by KingArthur10 on 2006-10-25
The wireless card should have been detected and loaded by default.  TO check it out, go to your system menu, admin, networking.  It should have a wireless connection there.  Click on it and click properties.  If the connection is not enabled, enable it.  Click on the arrow to the right of network name box, and it should have a drop down of networks.  Once you're connected to a network, I'd go and install network-manager-gnome from synaptic.  This will make it very easy to switch from one wifi network to another.

---

### Post by fngaserin on 2006-10-25
Ok... I have done what you told me but I still can't connect to the network via Wireless.

I'm using an Aztech 600EL DSL modem/router with wireless capability. I'm setting the security to a WEP with a Shared authentication type.I set the encryption key to 128-bit, rather than the normal 64-bit. Do you think that might have an effect. This time, I'm not loading acerhk at all, so I guess acerhk has nothing to do with it.

Any solution?

---

### Post by fngaserin on 2006-10-25
This is what I did...

```
sudo ifconfig eth1 down
sudo iwconfig eth1 essid XXXXX
sudo iwconfig eth1 key restricted s:XXXXXXXXXX
sudo ifconfig eth1 up
sudo dhclient eth1
```

And voila... it works perfectly... I guess it must be the restricted keyword that's important. Thanks for the help anyways. I appreciate it.

---

### Post by fngaserin on 2006-10-25
I've installed network-manager-gnome, however I don't know how to get it to run. Can I get some help on it?

---

