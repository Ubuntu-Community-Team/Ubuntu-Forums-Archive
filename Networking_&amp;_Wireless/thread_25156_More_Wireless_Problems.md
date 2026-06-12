---
title: "More Wireless Problems"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by calyx on 2005-04-09
I realise that this seems to be a reasonably common complaint, but even with google and searching these forums I haven't had any luck.

My problem is with the LinkSys WPC54G WiFi card for my laptop. I'm not very knowledgable with Linux, but I'm not new to Ubuntu. I had the card working perfectly in the last release (warty) using the windows drivers and ndiswrapper and specifiying the dns nameservers'.

But now, after formatting the partition and installing Hoary - and doing what I did last time to install the drivers, I can't access the internet. I tried "iwlist wlan0 scan" but that couldn't find my wireless router. I can't even ping any i.p.s. I can access the net fine when I plug the laptop directly into the router.

Can anbody help? I have no idea what's wrong.

---

### Post by az on 2005-04-09
What does ifconfig and iwconfig say?

If you go into the networking GUI, do you have a wireless entry?  Can you configure your essid and wep there?

---

### Post by calyx on 2005-04-09
Ifconfig says:

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:2E:7B:25
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:d0100000-d0101fff

iwconfig says:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:17 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


There is an entry in the networking gui, and it doesn't seem to have any problem activating/deactivatin the card.

---

### Post by Dillius on 2005-05-02
What was the name of the INF file you used to get this to run?

I am trying to get a WPC54G v.2 working, and no matter what I do ifconfig and iwconfig never show a wlan0 interface. However, Ndiswrapper detects the driver and matching hardware correctly. I'm really at a loss of what to do with it.

---

