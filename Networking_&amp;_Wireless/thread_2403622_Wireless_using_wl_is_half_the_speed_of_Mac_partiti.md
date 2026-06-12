---
title: "Wireless using wl is half the speed of Mac partition | BCM4331 (rev 02)"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by bennywas on 2018-10-13
BCM4331 (rev 02), Ubuntu 18.04 LTS
wireless info script: [http://paste.ubuntu.com/p/brddcV3qhs/](http://paste.ubuntu.com/p/brddcV3qhs/)

Wifi on my Ubuntu partition's wl driver is significantly slower than wifi on my macOS partition. I've controlled for everything. At the same time of the day, in the same spot, at the same wifi location (be it my house or the library or multiple cafes), with nothing else running, wl is consistently ~half the speed as macOS. Here are some test results from my house's 5G network, for example:
t1 [Ubuntu]("https://speedof.me/show.php?img=181012213936-5588.png")        88.6 Mbps&#10515;      13.23 Mbps&#10514;
     [macOS]("http://speedof.me/show.php?img=181012214202-5490.png")    125.58 Mbps&#10515;      88.97 Mbps&#10514;
t2 [Ubuntu]("https://speedof.me/show.php?img=181012214635-6645.png")        76.4 Mbps&#10515;      13.85 Mbps&#10514;
     [macOS]("https://speedof.me/show.php?img=181012214958-4829.png")    129.25 Mbps&#10515;      66.98 Mbps&#10514;
t3 [Ubuntu]("https://speedof.me/show.php?img=181012215325-9134.png")      73.15 Mbps&#10515;      12.77 Mbps&#10514;
     [macOS]("https://speedof.me/show.php?img=181012215609-2776.png")    134.95 Mbps&#10515;      87.82 Mbps&#10514;

I don't know an equivalent of lspci for Mac terminal; but, "About this Mac...More Info" reads:
Card Type:         AirPort Extreme (0x14E4, 0xEF)
Firmware Version:  Broadcom BCM43xx 1.0 (7.21.190.18.1a3)

Why is wl on Ubuntu so comparatively slow? And I know, 80 Mbps at home isn't much to complain about, but I'm usually working at cafes where even the maximum potential on my macOS partition isn't fantastic.

I'd like to optimize/troubleshoot the wl driver so it's as fast (or even nearly as fast) as my macOS partition. Please don't recommend b43 as a solution--I've had huge troubles with b43 and I'm actually going to make a separate post about it. (...And for the record, I have the exact same setup as the example in [help.ubuntu.com's bcm43xx page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), and they use the wl driver, so there.)

Thanks. :)

---

### Post by chili555 on 2018-10-13
Please consult the sticky: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) I believe you are using the incorrect driver.

Also, we see this:> Cell 01 - Address: <MAC 'Sonic-4934-5G' [AC1]>
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Sonic-4934-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKPlease check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

### Post by wildmanne39 on 2018-10-13
Please do:
```
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer
Reboot and let us know if it is better.

```
Thanks

---

### Post by bennywas on 2018-10-14
> **I'd like to optimize/troubleshoot the wl driver** so it's as fast (or even  nearly as fast) as my macOS partition. **Please don't recommend b43 as a  solution--I've had huge troubles with b43 and I'm actually going to make  a separate post about it.** (...And for the record, I have the exact same  setup as the example in [help.ubuntu.com's bcm43xx page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), and they use the wl driver, so there.)
...
> I believe you are using the incorrect driver.
> Please do:
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer

Unless these responses were made in haste, I must conclude:
- It is impossible to optimize the wl driver. No steps can be taken to troubleshoot its performance.
- BCM4331 (rev 02) should never be used with the wl driver&#8212;despite the fact that [Linux Wireless's page on b43]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/") *does* recommend wl as an alternative for this chipset.

If this isn't what you meant, please clarify.

---

### Post by chili555 on 2018-10-14
Many years of experience and thousands of forum posts have convinced many of us that wl is not optimal. However, I'm not a developer; I'm basing my post above on empirical evidence only.

Aside from the changes at the router that I suggest above, I know of no other steps to optimize wl. Did you try them?> I've had huge troubles with b43 and I'm actually going to make a separate post about it. It seems that your experience with wl is a bit troublesome as well.

There are a few Broadcom devices for which either driver works, just like your 4331. In almost every case, one or the other works a bit better. For your 4331, we think it's b43. However, today is a new day and we are always open to learn something new. Prove us wrong!

If I were in your shoes, I'd get to the router's administration pages and make the changes I suggest and test and report back. Let's go from there.

---

### Post by wildmanne39 on 2018-10-14
>  If I were in your shoes, I'd get to the router's administration pages and make the changes I suggest and test and report back. Let's go from there. 
+1, if you are determined to use the wl driver do what chili555 suggests then he can make recommendations from there about driver trouble shooting, he is the best with networking issues in the linux community, notice I did not just say ubuntu or ubuntu forums community.

---

### Post by bennywas on 2018-10-14
**Firstly:** *is b43 even supposed to work on BCM4331 (rev 02)?* The problems I'm about to describe are confusing enough to make me think it isn't. Plus,
- The example in [help.ubuntu.com's bcm43xx guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") has my exact same card, and it shows that the user is using wl, not b43.
- The supported devices chart in [Linux Wireless's b43 guide]("http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/")  says "Yes (3.2-rc3+)". ...Is "3.2-rc3+" referring to the card's  revolution number, or to the b43 version? If it's the card's revolution  then this question is already a dead end because the BCM4331 on my MBP  10,1 is "rev 02", not higher than 3.2.
- Using [FONT=courier new]dpkg -s firmware-b43-installer[/FONT], the "Supported chipsets" section doesn't mention 4331.
```

Package: firmware-b43-installer
Status: install ok installed
Priority: optional
Section: contrib/kernel
Installed-Size: 27
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: b43-fwcutter
Version: 1:019-3
Replaces: firmware-b43-lpphy-installer (<= 1:015-14)
Depends: b43-fwcutter (>= 1:019-3), bzip2, wget
Breaks: firmware-b43-lpphy-installer (<= 1:015-14)
Description: firmware installer for the b43 driver
 This package downloads and installs the firmware needed by the b43
 kernel driver for some Broadcom 43xx wireless network cards.
 .
 Supported chipsets:
  * BCM4306/3;
  * BCM4311;
  * BCM4318;
  * BCM4321;
  * BCM4322 (only 14e4:432b);
  * BCM4312 (with Low-Power a.k.a. LP-PHY).
Original-Maintainer: Daniel Echeverry <epsilon77@gmail.com>
Homepage: http://wireless.kernel.org/en/users/Drivers/b43

```

**Now, for the juice.** Wireless info script: [http://paste.ubuntu.com/p/brddcV3qhs/](http://paste.ubuntu.com/p/brddcV3qhs/)
Before I go on, let me mention that when bcmwl-kernel-source is  installed, the driver in use at boot is wl and it works fine (although  it's half as fast as my macOS partition). Example of wl in action:
```

benny@benny-MacBookPro:~$ lspci -vvnn | grep -A 9 Network
04:00.0 Network controller [0280]: Broadcom Limited BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c1900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: bcma, wl
benny@benny-MacBookPro:~$ lsmod|grep wl; lsmod|grep bcma; lsmod|grep b43
wl                   6447104  0
cfg80211              622592  1 wl
benny@benny-MacBookPro:~$
benny@benny-MacBookPro:~$ ######  speedof.me results  ######
benny@benny-MacBookPro:~$ # LATENCY    DOWNLOAD    UPLOAD
benny@benny-MacBookPro:~$ # 15ms       29.83Mbps   12.28Mbps
benny@benny-MacBookPro:~$ # 16ms       48.03Mbps    7.13Mbps
benny@benny-MacBookPro:~$ 
benny@benny-MacBookPro:~$ # I can unload wl without a problem.
benny@benny-MacBookPro:~$ sudo modprobe -r wl
[sudo] password for benny: 
benny@benny-MacBookPro:~$ lsmod|grep wl; lsmod|grep bcma; lsmod|grep b43
benny@benny-MacBookPro:~$ 

```

**I've already tried to install b43 and its firmware**, i.e. firmware-b43-installer (which includes b43-fwcutter; I checked),** but I can't switch to it because [FONT=courier new]modprobe b43[/FONT] always loads bcma-pci-bridge. **It's supposed to load b43-pci-bridge, I'm pretty sure.
Now  the same problems come up regardless of whether bcma-kernel-source is  purged and/or b43 or bcma are blacklisted. I've tried every combo, but  I'm just gonna give you some examples. (By the way, I *am* using sudo for all these commands, even if I don't mention it.)...

Ex. 1: With bcmwl-kernel-source installed (and nothing blacklisted), I can successfully [FONT=courier new]modprobe -r wl[/FONT]. Fom here, attempting to [FONT=courier new]modprobe b43[/FONT] instead loads the "Kernel driver in use" as "bcma-pci-bridge", and [FONT=courier new]lsmod[/FONT] returns the following:
```

benny@benny-MacBookPro:~$ lsmod|grep bcma; lsmod|grep b43; lsmod|grep wl
bcma                   57344  1 b43
b43                   413696  0
mac80211              778240  1 b43
cfg80211              622592  2 b43,mac80211
ssb                    57344  1 b43
bcma                   57344  1 b43
benny@benny-MacBookPro:~$

```
From here, [FONT=courier new]modprobe -r bcma[/FONT] returns "modprobe: FATAL: Module bcma is in use." It's in use by b43, I see. And [FONT=courier new]sudo kill -9[/FONT]  doesn't work on any of these processes; trying to do so returns "kill:  (57344): No such process" for some reason. If instead I try to [FONT=courier new]modprobe -r b43[/FONT], it will return "Segmentation fault (core dumped)" and one or more of the following will occur:
-  The "Update-notifier" app will pop up several minutes later with a  dialogue: "System program problem detected. Do you want to report the  problem now?" (Yes) Immediately after, "Report a problem..." app pops up  with a dialogue: "Sorry, Ubuntu 18.04 has experienced an internal  error. Send problem report to the developers?" (Yes).
- [FONT=courier new]$ poweroff[/FONT]  hangs at the the logo screen with the white dots loading indefinitely. I  have to manually hold the power button to power off when this happens.
- Terminal will hang on something and not un-hang itself.
When any of the above happens, manually powering off then on again resolves it and everything is back to normal at boot.

Ex. 2: With bcmwl-kernel-source purged (and nothing blacklisted), the default driver in use is "bcma-pci-bridge" and [FONT=courier new]lsmod[/FONT]  shows that b43 stuff is loaded too, just like above. Again, I can't  remove or kill anything without the same problems, and manually  rebooting brings me back to normal.

Ex. 3:  With  bcmwl-kernel-source purged, and both b43 and bcma blacklisted in  /etc/modprobe.d/blacklist.conf, the default driver in use is STILL  "bcma-pci-bridge", but now with no b43 stuff loaded. From here I can  actually remove bcma successfully. However, even from this blank slate, [FONT=courier new]modprobe b43[/FONT]  again loads "bcma-pci-pridge" with b43 loaded (just like Ex. 1 &  2). Again, I can't remove or kill anything without the same problems,  and manually rebooting brings me back to normal.

In terms of speed / the success of my wireless connection...
- wl worked fine (though ~half the speed as my macOS partition)
-  bcma-pci-bridge with b43 loaded actually does allow for a connection,  but it's marvelously slow. Like, a snail stumbling through the fog of a  monday morning without coffee slow. (The speedof.me webpage loaded but  refused to test lol; I've tried before with this as the setup and it's  usually under 1 Mbps)
- bcma-pci-bridge without b43 loaded has no connections. Settings shows "No Wi-Fi Adapter Found".
- I can't load b43 (b43-pci-bridge?) by itself, obviously, so I couldn't tell you how fast that would be.

**Possible solutions/answers?**
1.  If I can permanently put bcma-pci-bridge out of its misery, then maybe  loading b43 will stop triggering bcma as well and b43-pci-bridge will  actually show up for once. But I don't know how to block bcma like that.  Could I purge it? Could I put it in another blacklist?
2. Maybe  firmware-b43-installer isn't actually the correct firmware or driver for  BCM4331 (rev 02); maybe I'm supposed to have b43legacy or something.  Although none of the support pages mention that for my chipset.
3.  Maybe b43 really isn't supposed to work with my chipset at all, and I  should stick with using wl and try to optimize its speed so it's not  half as fast as my macOS partition.

---

### Post by jeremy31 on 2018-10-14
bcma works with b43 and the firmware for your chipset, do a code ```
modprobe -c | grep -i 14e4 | grep 4331
```

If you are still having issues see the wireless script link in my signature and post results

---

### Post by wildmanne39 on 2018-10-14
Threads merged since it is dealing with the same issue and the same volunteers will be answering this thread as the other one, please do not create more then one thread on the same topic it creates confusion and dilutes community effort, I realize you may think they are different but they really are not.

---

### Post by chili555 on 2018-10-14
> Is "3.2-rc3+" referring to the card's revolution number, or to the b43 version?

The kernel version. That should tell you how old the document you are referencing really is. We are now running 4.15.

> I've already tried to install b43 and its firmware, i.e. firmware-b43-installer (which includes b43-fwcutter; I checked), but I can't switch to it because modprobe b43 always loads bcma-pci-bridge. It's supposed to load b43-pci-bridge, I'm pretty sure.

I’m pretty sure not. Let’s look at: ```
modinfo b43:
```

```
depends:        mac80211,ssb,bcma,cfg80211

```
So, when the kernel sees the pci.id for your device, 14e4:4331, it loads bcma. All its cousins; namely mac80211, ssb, b43 and cfg80211 jump in, too. 

As for the driver being referred to in lshw as bcma-pci-bridge, that’s a mystery to me. You may also notice that bcmwl-kernel-source shows in lsmod as wl; it shows in lshw as wl0. Do I think it is, in any way, significant? No.

> and b43-pci-bridge will actually show up for once.

There is no b43-pci-bridge that I’ve ever seen.

> Maybe firmware-b43-installer isn't actually the correct firmware or driver for BCM4331 (rev 02); maybe I'm supposed to have b43legacy or something. Although none of the support pages mention that for my chipset.

Modinfo bcma says:

```
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F4DB57748318105D28C557A
<snip>
alias:          pci:v0000[COLOR="#FF0000"]14E4[/COLOR]d0000[COLOR="#FF0000"]4331[/COLOR]sv*sd*bc*sc*i*

```
So, yes, it will drive your device. As well as wl? Only you can tell us.

> bcma-pci-bridge with b43 loaded actually does allow for a connection, but it's marvelously slow. Like, a snail stumbling through the fog of a monday morning without coffee slow. (The speedof.me webpage loaded but refused to test lol; I've tried before with this as the setup and it's usually under 1 Mbps)

Is there any improvement with the changes in the router I recommend?

---

### Post by bennywas on 2018-10-15
I now understand that the b43 module depends on the bcma module, as well as those other "cousins". However, I'm under the impression that...
-- Regardless of what modules are in use, only one wireless driver can actually drive a device at a time.
-- b43 is a driver. bcma is a driver. wl is also a driver. These are three, separate wireless drivers.
-- lspci's "Kernel driver in use" displays the driver which is currently behind the wheel, so to speak.
-- lspci's "Kernel modules" lists the modules installed which can be loaded as drivers. For example... "bcma" is here, and it seems to load the driver "bcma-pci-bridge" when I modprobe it. "wl" is here, and it seems to load the driver "wl" when I modprobe it.
-- Therefore, since b43 is a driver, first of all it seems like there should be something b43-related in lspci's "Kernel modules". Even if not, it certainly seems like modprobe b43 should load a b43-related driver (whatever its name is) and that driver be displayed in lspci's "Kernel driver in use". (I got "b43-pci-bridge" by browsing BCM43xx threads [like]("https://askubuntu.com/questions/393936/broadcom-b43-driver-again-why-modprobe-b43-manually") [these]("https://bbs.archlinux.org/viewtopic.php?id=176625").)
-- The above isn't happening when I modprobe b43. No matter what I try, it looks like bcma is still doing the driving instead of b43.
Is my thought process mistaken somewhere? /Where?

> Is there any improvement with the changes in the router I recommend?
Actually, I'm trying to optimize my connection given that:
-- Router settings are (usually) out of my hands. I do most of my work in cafes and libraries, and while my original post mentions my house's wifi, the house's router (and messing with it) belongs to the landlord. I asked him if he'd please switch the encryption to WPA2-AES, which he'll probably do because it's an easy sell and not difficult to change&#8212;as opposed to those other tweaks you mentioned, which look tasty but are a harder sell and require a lot more thinking/knowledge to change.
-- The differences in speeds I've noticed are consistent regardless of what router/network I'm on. At any given location, this seems to be the case: my macOS partition will be at a certain nice speed ("100%"); Ubuntu's wl driver will be at a slower speed ("50%"); Ubuntu's bcma-pci-bridge driver with b43 in use will be at a reaaaalllly slower speed ("10%"); Ubuntu's bcma-pci-bridge driver alone shows no networks; and I still can't figure out if (or how) I can make b43 do the driving.

I'll use [testmy.net's automatic speed test]("https://testmy.net/auto") over the next few days to thoroughly compare each driver/module combination and confirm the above. The bcma/b43 situation is still unclear to me so I'll hold off on those until you recommend what's what.

---

### Post by jeremy31 on 2018-10-15
There is a difference, b43 works fine with bcma and ssb, but those conflict with wl.  It is because b43 depends on bcma and ssb but not wl.

---

### Post by chili555 on 2018-10-15
> Is my thought process mistaken somewhere? /Where?
Yes. bcma is not a seperate and distinct driver from b43. b43 is actually the driver and bcma and others are its dependencies. You can have *both* or *neither*.

I understand that you have issues getting the landlord to change. The cafes and libraries, of course, will never change.

All we can do is suggest all the fixes we are aware of. Linux wireless networking is tricky. We haven't the means to make it just as good as Mac OS or Windows. In fact, some wireless devices and drivers, notably Intel, seem to work just the same or maybe better in Linux as in Windows. 

If yours is the exceptional case where wl/cfg80211 works better than bcma/b43/ssb/cfg80211/mac80211 then, by all means, use it.

Here is something to show the landlord about TKIP: [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)> TKIP itself is no longer considered secure, and was deprecated in the 2012 revision of the 802.11 standard.And here is an interesting thread about auto channel select: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

---

