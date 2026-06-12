---
title: "Strugling with Wifi"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by stigolike on 2007-04-01
Hi,

I'm new to Linux and Ubuntu and have searched for help over the last couple of days for help in getting my 3com wireless card to work with my Toshiba Satellite pro laptop.

I get an error of 

prism54: Your card/socket may be faulty, or IRQ line too busy 

when I use the msesg command

I'm not really sure why I can't get the card to activate. I've tried using the Fn + Fkey to turn on the wifi for the laptop but this doesn't appear to be working

The Prism54 driver appears to be installed and working.

My network is using a WEP key and a DHCP server. I would like to retain theses settings as I have other windows devices which also connect through the same router.

Please HELP!!!

---

### Post by Kobalt on 2007-04-01
Can you please post the outputs of the following two command line : 
```
iwconfig
lspci
```
That way we'll know if your card is installed and set up properly and its exact model.

---

### Post by stigolike on 2007-04-01
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      NOT READY!  ESSID:"3com"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
03:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)
05:00.0 USB Controller: NEC Corporation USB (rev 43)
05:00.1 USB Controller: NEC Corporation USB (rev 43)
05:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

---

### Post by Kobalt on 2007-04-01
> **stigolike said:**
> 
eth2      **NOT READY!**  ESSID:"3com"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It does seem your card isn't configured properly (it'a 3crwe154g72 by the way). 
Here is a thread that explains how to get the card working using ndiswrapper and the windows drivers : [http://www.ubuntuforums.org/showthread.php?t=156710](http://www.ubuntuforums.org/showthread.php?t=156710)
It's talking about a WPA connection and since you say you want to keep you WEP key, just skip the steps 12, 13 & 17 and you'll be just fine.

---

### Post by stigolike on 2007-04-01
Ok, thanks will try and give it a go...

---

### Post by bearbottoms on 2007-04-01
> **Kobalt said:**
> It does seem your card isn't configured properly (it'a 3crwe154g72 by the way). 
Here is a thread that explains how to get the card working using ndiswrapper and the windows drivers : [http://www.ubuntuforums.org/showthread.php](http://www.ubuntuforums.org/showthread.php)
It's talking about a WPA connection and since you say you want to keep you WEP key, just skip the steps 12, 13 & 17 and you'll be just fine.

That link didn't work!

---

### Post by Kobalt on 2007-04-02
Oops, sorry!

Here is the correct link : [http://www.ubuntuforums.org/showthread.php?t=156710](http://www.ubuntuforums.org/showthread.php?t=156710)

---

### Post by stigolike on 2007-04-02
Many thanks for your help.

After many trials and tribulations I finally have my wifi card working correctly using a self compiled ndiswrapper, and I have to say I'm really pleased with the performance.

Really appreciated

:)

---

### Post by Kobalt on 2007-04-02
You're very welcome ;)

---

