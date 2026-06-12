---
title: "ndiswrapper problems for Belkin PCMCIA F5D7010au WiFi card using Edgy"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by drahmad on 2007-01-30
Sorry, reposting here as this might be the more correct place for it:

Hi, and thanks in advance. Am having frustrating problems getting this card to run on my Ubuntu 6.10 system.

I have read widely about my card, which is a Belkin F5D7010au (version 3000au).

This is the guide I have been mainly using:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

As instructed (because I'm using Edgy), I installed ndiswrapper-utils-1.8 instead of the ndiswrapper-utils package. And then I forced the install of ndisgtk_0.6-0ubuntu1_all.deb using the "--force-depends" command.

However I got an error about dependencies that I then corrected (perhaps I was supposed to just leave this?)

Then I installed the bcmwl5a.inf driver as I believe works with my card. The first time I used "ndiswrapper" but then realised it was supposed to be "ndiswrapper-1.8" instead. So I uninstalled the driver and then reinstalled using ndiswrapper-1.8.

```
ndiswrapper -l
```
gives me:

Installed drivers:
bcmwl5a         driver installed 

(ie. no mention of "hardware present")

This is the log output showing what happens when my card is inserted:

Jan 30 17:47:15 thinkpad kernel: [  555.872378] pccard: CardBus card inserted into slot 0
Jan 30 17:47:15 thinkpad kernel: [  555.874671] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Jan 30 17:47:15 thinkpad kernel: [  555.874705] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

System/Admin/Networking shows "a card" (is the system loading a generic driver which is interefering?? I have already blacklisted bcm43xx). But ndisgtk says "hardware present: no" under bcmwl5a.

More outputs:

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My hypothesis is that the "plug and play" generic driver (which didn't work when I tried to configure it using System/Admin/Networking) is still being loaded and interferes with the "correct" driver that I'm trying to install?

Please help me. I'm losing sleep over this :/

---

