---
title: "Wireless problems on Acer Aspire 3100 - no network card found (noob)"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Tomkin on 2007-09-30
I just got a shiny new Acer Aspire 3100, and installed Kubuntu 7.04 on it right away. Unfortunately, I can't for the life of me figure out what's wrong with my wireless. The system is detecting eth0, but not eth1. Wireless Assistant won't detect any wireless devices. Lspci is as clear as mud, but shows not network controller that I can see. Here's its output:

> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

If that contains any wireless stuff, I don't see it. So my question is, what do I do now? Thanks for the help!

 - Tomkin

---

### Post by Natr0n on 2007-09-30
> 02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01) There's the wireless adapter. Madwifi should work for your adapter. I have an Atheros Wireless adapter too and haven't had any problems. Also, the connection would be called ath0 not eth1. Try running the command iwconfig and posting the output.

EDIT: Also try ```
$ ifconfig ath0
``` and post the output.

---

### Post by Tomkin on 2007-10-01
Both before and after getting madwifi, this is the output of iwconfig and ifconfig:

> name-removed@name-removed:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
name-removed@name-removed:~$ ifconfig ath0
ath0: error fetching interface information: Device not found

That seems to be a problem. How do I get it to recognize ath0?

Thanks!
 - Tomkin

---

### Post by tdrusk on 2007-10-01
I have an acer aspire 3680. Mine came up with the same thing. I used this to make my wireless work.

[http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680](http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680)

---

### Post by Tomkin on 2007-10-01
I followed the instructions, as well as installing wicd. I like wicd, but it claims "no wireless networks found". And iwconfig and ifconfig still output the same.

Thanks for your help, though! Something funky is going on, because Vista can find my wireless... :( So I know it's not a defective card.

 - Tomkin

---

### Post by tdrusk on 2007-10-01
run
```
sudo update-pciids
```
Now run lscpi.
If your card matches the one in the guide I posted use it.

---

### Post by Tomkin on 2007-10-01
After runing update-pciids, lspci now outputs this:

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Is that that similar enough that I should still use the guide? Sorry for being so noobish.

On an almost completely unrelated note, where do I tell the computer to execute the wicd-tray command so that it runs on startup?

Thank you so much for your time. I really appreciate it. People like you are one of the main reasons I use Ubuntu.
 - Tomkin

---

### Post by tdrusk on 2007-10-01
> **Tomkin said:**
> After runing update-pciids, lspci now outputs this:

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Is that that similar enough that I should still use the guide? Sorry for being so noobish.

On an almost completely unrelated note, where do I tell the computer to execute the wicd-tray command so that it runs on startup?

Thank you so much for your time. I really appreciate it. People like you are one of the main reasons I use Ubuntu.
 - Tomkin

This is derived from the guide. I wrote it out. It worked perfectly for me.

Open a terminal and paste
```
wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz && tar xvf atheros-ar5007eg-installer-0.1c.tar.gz && sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential && echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist && pushd atheros-ar5007eg-installer-0.1c/ndiswrapper-1.48/ && sudo make uninstall && make && sudo make install && popd && pushd atheros-ar5007eg-installer-0.1c/ar5007eg/ && sudo ndiswrapper -i net5211.inf && popd && sudo modprobe ndiswrapper && echo "ndiswrapper" | sudo tee -a /etc/modules && sudo init 6
```

---

### Post by Tomkin on 2007-10-01
It still doesn't work...

Well, I can live without wireless for a while. Thanks for your help anyway!

 - Tomkin

---

### Post by tdrusk on 2007-10-01
> **Tomkin said:**
> It still doesn't work...

Well, I can live without wireless for a while. Thanks for your help anyway!

 - Tomkin

woah woah woah...
did you run the command I put in my previous post?

If so, try messing with the switches on the front. One is bluetooth, the other is wireless. Bluetooth doesn't work, so it doesn't hurt to switch either one.

---

### Post by Tomkin on 2007-10-01
Yes, I did, twice. It had no effect. Is it possible that I need a different driver?

Thanks!
 - Tomkin

---

### Post by tdrusk on 2007-10-01
I'm not sure why my command wouldn't work, but try the guide if you haven't already. 

We have the same exact card. It should work.

---

### Post by Tomkin on 2007-10-01
Ah, here we go.
I manually downloaded the Windows XP driver from the Acer website, bonked ndiswrapper on the head until it installed it, and now ifconfig outputs this:
```
eth0      Link encap:Ethernet  HWaddr 00:16:D4:D1:D1:F2
          inet addr:192.168.15.101  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fed1:d1f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:207255 (202.3 KiB)  TX bytes:12222 (11.9 KiB)
          Interrupt:21 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:7E:3D:D2:1D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:54000000-54010000

wlan0:ava Link encap:Ethernet  HWaddr 00:19:7E:3D:D2:1D
          inet addr:169.254.5.166  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:54000000-54010000

```
And iwconfig this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Some progress! Yay! Wicd still can't find wireless, though.

Thanks,
 - Tomkin

---

