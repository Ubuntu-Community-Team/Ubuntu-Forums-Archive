---
title: "Wireless Internet Problems"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by alon_lhv on 2008-12-07
For few days now I am having a problem connecting my old laptop to the Internet. I tried to get some advices in this forum, but until now- I didn't success to sole my problem.

The background: I have an IBM Thinkpad T20 700MHz with 256MB RAM and 20 GB HD. Ubuntu 8.04 is installed on it (not by me). The network name is "LahavNet" and it is not encrypted. The USB adapter is NETGEAR WG111v2. The Internet connection works well for 1-10 minutes after restarting my computer, and then it looses it's connection. When I used the USB adapter in my other laptop, it worked well (with Vista).

Here is the results for all my checking, that I've done by your advices:
1) Using: "lshw -C network", I learned that my wireless device's logical name is: "wlan0".
2) Using: "iwconfig", I gut:
...
wlan0 IEEE 802.llg ESSID:"LahavNet"
mode:Managed Frequency:2.412GHz Access Point: 00:14:d1:5:bf:ee
Bit Rate=1 MB/s Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragmented thr=2346 B
Link Qaulity=57/64 Signal Level=46/65
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retris:0 Invalid misc:0 Missed beacon:0
3) After using: "sudo iwconfig wlan0 rate 11M" nothing changed.
4) Using: "sudo iwlist scan", I sometimes get:
```
lo Interface doesn't support scanning.
irda0 Interface doesn't support scanning.
wmaster0 Interface doesn't support scanning.
wlan0 No scan results
```
And sometimes get:
```
lo Interface doesn't support scanning.
irda0 Interface doesn't support scanning.
wmaster0 Interface doesn't support scanning.
wlan0 Scan completed :
Cell 01 - Address: 00:141:55:BF:EE
ESSID:"LahavNet"
Mode:Master
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=58/64 Signal level=45/65
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:tsf=00000023a48761cc
Cell 02
....
```

So, what can we do now??? I hope this problem can be solved ..

---

### Post by slammed87d21 on 2008-12-08
From what I Googled, it seems there is a problem with the Madwifi drivers Try downloading Ndiswrapper. Seems like it works better. Heres the link for the Windows driver. You just need to know what version to get.[http://kbserver.netgear.com/products/wg111v2.asp]("http://kbserver.netgear.com/products/wg111v2.asp")

---

### Post by alon_lhv on 2008-12-08
OK, as a new guy in this linux world, it took me a while to understand what you ment... I've installed Ndiswrapper, and downloaded the latest netgear driver. But the driver is "setup.exe" and Ndiswrapper must have files .sys and .inf. Did I miss something?
Thanks.

---

### Post by alon_lhv on 2008-12-08
I succedded to install the driver, but it still doesn't work well: it works good after restart, but after a while the Internet is out of reach .. :(

---

### Post by slammed87d21 on 2008-12-09
Sorry it took so long to get back. Did the driver have more than one .inf file? If it did try the other.

---

### Post by rev0lv3r on 2008-12-10
You might also want to check if 8.10 has those drivers already put into the kernel or something

I found that on one of my computers, a lot of the wireless issues went away by installing a fresh 8.10 (it used to run 7.10).

---

### Post by alon_lhv on 2008-12-11
Thanks for the last advice. I tried the live CD of Ubuntu 8.10 it it looks like it work well. I hope it will be stable too. Tomorrow I will upgrade my old laptop. I'll let you know the results..

---

### Post by alon_lhv on 2008-12-12
> **rev0lv3r said:**
> You might also want to check if 8.10 has those drivers already put into the kernel or something

I found that on one of my computers, a lot of the wireless issues went away by installing a fresh 8.10 (it used to run 7.10).

Thank you very much, it helped!

---

