---
title: "Acer Laptop and Broadcom 4318 Wireless problems"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by KoldKay on 2007-04-22
Hi all, I've tried quite a lot of the tutorials on here.. and it just isn't happening.

For reference, I'm on 7.04 Kubuntu and I have an Acer Aspire 5051AWXMi.  My wireless network is on a Netgear router with a simple WEP key.

I've tried various approaches, but my last one was such: I used fwcutter to try and install my Broadcom 4318.  I get the following from iwconfig:
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm just not getting anything.  I also tried to follow this for acer laptops here: [http://ubuntuforums.org/showthread.php?t=224350]("http://ubuntuforums.org/showthread.php?t=224350")

I can't find any wireless networks.  I've tried rebooting etc.  Any help would be much appreciated, even if its just links to guides that can help.

---

### Post by srt4play on 2007-04-22
[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by KoldKay on 2007-04-23
> **srt4play said:**
> [http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

Hi, thanks for this but it didn't really work. :)

In the end, I found this on the ubuntu guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset")

If anyone else has a Broadcom 43xx chipset, I recommend the automatic installer referenced there [http://student.khleuven.be/~501115/bcm4318.Feisty.tar.gz]("http://student.khleuven.be/~501115/bcm4318.Feisty.tar.gz")

It automatically installed everything.  After spending roughly 5-6 hours of forum trawling, this is the only option that's worked for me.

---

### Post by srt4play on 2007-04-23
> **KoldKay said:**
> In the end, I found this on the ubuntu guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset")

If anyone else has a Broadcom 43xx chipset, I recommend the automatic installer referenced there [http://student.khleuven.be/~501115/bcm4318.Feisty.tar.gz]("http://student.khleuven.be/~501115/bcm4318.Feisty.tar.gz")

It automatically installed everything.  After spending roughly 5-6 hours of forum trawling, this is the only option that's worked for me.

Works for me every time, you did the same steps only you got the windows drivers from a different place.  Glad you got it working.

---

### Post by vorlich on 2007-04-25
I have an acer aspire 3620 which worked fine in Edgy. When I followed the wireless install using the new feisty BCM 4318 driver and acer_aspire .0.4 every works fine for a moment or two before the key board and the screen crash and the laptop has to be re-booted with a power  off.

This never happened in the previous version so I was wondering if this is bug or does anyone have an idea what causes the crash. I haven't read the logs yet cos I have had enough of it for one night and I am seriously considering re_installing the Edgy version

Oh and I have tried this with both the Ubuntu distro and the Xubuntu which is why I guess it is either a bug or an issue with the new driver.

---

### Post by Melcar on 2007-04-25
Use ndiswrapper.

- First you should compile ndiswrapper from source;
          + Download ndiswrapper [http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/")
          + Follow steps 11-14 [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

- Follow this guide (it works for my 4318 as well) [http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+with+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+with+ndiswrapper")

---

### Post by vorlich on 2007-04-26
Thanks. Excellent advice which I appreciate. I had a quick look through those pages and they seem to have all the info I need. Looks like I will not need to re-install the older version.

---

### Post by bedfojo on 2007-04-26
Just for the record, I have an Acer Aspire 3613WLMi with the Broadcom 4318 chipset. I use a WPA wifi network.

It worked fine under Egdy, but was completely borked on a clean Feisty install.

I finally got it sorted (mostly) by removing the Feisty ndiswrapper (1.38 ), compiling myself the latest ndiswrapper (1.42), installing the driver from the Acer website (bcmwl5), removing Network-Manager completely and using Wicd instead.

All OK except that it still can't cope if I stop the router broadcating its SSID. 

It'd be nice if:
(1) Wicd was added to the Feisty repos,
(2) the latest ndiswrapper was added to the Feisty repos, and 
(3) the hidden SSID problem was fixed, but I reliase that the problem may be in ndiswrapper, wpa_supplicant or even the new kernel, and may not be as easy as (1) or (2).

---

### Post by Bruneauinfo on 2007-04-28
Worked great for me too! For WPA2 even.

I had a problem the first install of Feisty. But I did this guide after trying five other things that didn't work. So I think the combination of the other five tweaks made this last one unstable. I could be wrong about this though. I'll   post back if I note any deterioration since I've only had my wireless up for a few minutes.

However, I will add that on my last install this guide worked, but not with WPA2. Eventually it wouldn't work with WPA either after about 24 hours. This install worked with WPA2 right away with no hickups.

BTW: Broadcom 4318 Wireless on an Acer Aspire 3000 running Feisty 32 bit.

---

