---
title: "(sometimes!) my Intel 3945 wireless won't connect"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Duranxl on 2008-09-09
Hi all.

I'm having a problem with ubuntu & wireless.
Usually my internet works fine (using it now)..but sometimes it just won't connect.
The connecting-animation keeps going for a couple of minutes before it just stops.. none of the two 'balls' turn green. I put a 2nd laptop next to it with windows and it connects just fine. Also sometimes the wireless connection will just disappear from the list. (even though it's there on the windows laptop)
 
Once I reboot ubuntu, it usually works again.:confused:

I have no idea what's causing this..  i tried this program called wifi-radar but it doesn't seem to interact with the default wireless service.

Any help?
thanks!!

---

### Post by Duranxl on 2008-09-10
Bump, I'm on Windows at the moment because ubuntu -once again- didn't see my network.
I rebooted my laptop and booted XP (i have dualboot) and voila!, it worked instantly.

I'd really like to get this fixed, because this is causing me to choose XP upon boot..knowing that I might not have internet on ubuntu..
:(

edit: oh im using WICD right now, i like it better than the default (i can refresh!) but the problem persists

thanks

---

### Post by ALainONE on 2008-09-10
This happens when you boot on windows then on linux or vice versa...

The problem lies with windows keeping the drivers alive after restarting. It takes a couple of minutes for windows to release the drivers even after a restart.

So, if you booted on linux and restarted on windows, then restarted on linux... windows will try to deny access to your drivers.

The way out is to shut down, wait a couple of minutes then start with your linux - and don't go on starting your windows again! :)

---

### Post by Muflon on 2008-09-10
> **ALainONE said:**
> This happens when you boot on windows then on linux or vice versa...

The problem lies with windows keeping the drivers alive after restarting. It takes a couple of minutes for windows to release the drivers even after a restart.

So, if you booted on linux and restarted on windows, then restarted on linux... windows will try to deny access to your drivers.

The way out is to shut down, wait a couple of minutes then start with your linux - and don't go on starting your windows again! :)


Are you sure about this :confused:

---

### Post by mickyg on 2008-09-10
> **ALainONE said:**
> This happens when you boot on windows then on linux or vice versa...

The problem lies with windows keeping the drivers alive after restarting. It takes a couple of minutes for windows to release the drivers even after a restart.

So, if you booted on linux and restarted on windows, then restarted on linux... windows will try to deny access to your drivers.

The way out is to shut down, wait a couple of minutes then start with your linux - and don't go on starting your windows again! :)

I'll stand corrected (and *completely* baffled) on this but I'm pretty sure that Windows doesn't 'keep drivers alive' after a reboot. I think it's much more likely that your router is using the same channel as, or a channel close to, another wireless router within the same area as you. A possible reason that Ubuntu might be more effected than Windows by this could be to do with the sensitivity setting of your wifi card being different in Ubuntu than in Windows.

The sensitivity of the wifi card can be set in using the **iwconfig** application if it comes to that (read the man page and look for the **sens** argument). 

My advice in the first instance, before you start looking in to changing sensitivity settings, would be to scan for wireless networks using the **iwlist [interface] scan** command. This will show you all the other wifi networks detected and the channel/frequency they are using. You can then try changing the channel on your router to see if that works.

Hope that helps!

Please post back and let us know how you get on.

---

### Post by ALainONE on 2008-09-11
> **Muflon said:**
> Are you sure about this :confused:

I had encountered the same problem with my dv6000 notebook.  It was on dual-boot with XP and UE 1.8. I notice that every time I am running UE and restarted with my XP and restarted again with UE, some of my drivers are not being detected, the iwl3945 in particular, gets messed up.  That is restarting without powering off or shutting down...

But if I shutdown the notebook completely and wait a couple of minutes and boot only on my UE (and never using XP), everything is working well - wireless connects flawlessly and continuously.

Problem only occurs on my nix when I start using XP.  Probably some resident programs (or drivers) still lie in memory causing conflict with my UE to boot???  So, I removed my dual-boot and installed Ubuntu and did not have the problem again.

Just sharing my thoughts and what I had experienced...

---

### Post by Duranxl on 2008-09-12
Weird..
Well i've recently installed WICD...and i havent been able to do the IWLIST command because the problem hasn't occured since.
Either it's WICD (which has clearer interface anyway) or the fact that i haven't booted into windows for the last days.
Can't imagine how an OS can do anything to a driver when it's turned off

---

### Post by jasonkirk2006 on 2008-09-13
> **ALainONE said:**
> 
The way out is to shut down, wait a couple of minutes then start with your linux - and don't go on starting your windows again! :)

I can say that this is clearly not the case in my situation. I've been booting into linux for the last few days, without booting into Vista, and i'm having the same problem since the beginning. For example the last time i powered on my computer, i used Hardy (it was approximately 24 ours ago) and than shut it down after a few minutes. Then until now, it was closed, power cable was unplugged and the battery was removed - completely no power! Even now there is a wireless problem, which persists for some unknown reason.

Symptoms and the solutions (if any) vary widely. Some say that wicd performed well while others propose usage of disable_hw_scan, none of them work in my case.

---

### Post by ALainONE on 2008-09-14
> **jasonkirk2006 said:**
> I can say that this is clearly not the case in my situation. ***I've been booting into linux for the last few days, without booting into Vista, and i'm having the same problem since the beginning***. For example the last time i powered on my computer, i used Hardy (it was approximately 24 ours ago) and than shut it down after a few minutes. Then until now, it was closed, power cable was unplugged and the battery was removed - completely no power! Even now there is a wireless problem, which persists for some unknown reason.

Symptoms and the solutions (if any) vary widely. Some say that wicd performed well while others propose usage of disable_hw_scan, none of them work in my case.

Having the problem with your WiFi from the beginning?  Do you mean that it hadn't work since you started using your nix after installation?  Is your card being detected and is installed by ubuntu?  

```
ndiswrapper -l
```

Here's another simple solution to WiFi problems...  [[COLOR="Blue"]Thread here![/COLOR]]("http://ubuntuforums.org/showthread.php?p=5781069#post5781069") dvlong suggest [try] resetting your router!


.

---

### Post by jasonkirk2006 on 2008-09-14
> **ALainONE said:**
> Having the problem with your WiFi from the beginning?  Do you mean that it hadn't work since you started using your nix after installation?  Is your card being detected and is installed by ubuntu?  
.

Not exactly; it worked at random times. But the situation is very complex, i think. For example dmesg logs show this (for kernel 2.6.24-16):

```

$ dmesg | grep 3945
[   27.512434] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2d
[   27.512522] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   27.600370] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```

and show this (for kernel version 2.6.24-19)

```

$ dmesg | grep 3945
[ 3.088173] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[ 3.226360] iwl3945: MAC is in deep sleep!
[ 3.226431] iwl3945: Unable to int nic

```

and may sometimes show microcode error of some sort i cannot regenerate now.

And the lspci command perfectly lists the wireless card chipset as:

```

# lspci -vvn -s 0b:00.0
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1021
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 17
	Region 0: [virtual] Memory at f9eff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <128ns, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

```

and 3945 related modueles are listed at the output of lsmod command (for now ipw3945):

```

$ lsmod | grep 3945
ipw3945               199200  0 
ieee80211              35528  1 ipw3945

```

But lshw output sometimes show my wireless as "UNCLAIMED", and other times "DISABLED". This generally causes a situation where ifconfig -a command lists wlan0 having a MAC address of FF:FF:FF:FF:FF:FF. But again at random times, is works perfectly, seeing both WPA and WEP networks around.

I think the card is recognized, by the kernel but the driver is not associated with the card somehow. Or the card cannot be brought up from sleep situation.

I must add that the damn **_*Vista perfectly recognizes the card, accepts the supplied driver and can communicate with all kinds of networks around*_**.

I also tried iwl3945, ipw3945 and compat-wireless drivers with no avail.

The complexity probably gets bigger if it's a Dell XPS, as far as i can see.

> 
Here's another simple solution to WiFi problems...  [[COLOR="Blue"]Thread here![/COLOR]]("http://ubuntuforums.org/showthread.php?p=5781069#post5781069") dvlong suggest [try] resetting your router!

This is also my thread, which i check several times a day. I have tried several different routers and APs. This is not a router issue, for sure. If my card and its module was properly loaded, then i would think of a router issue. But now, it is not.

---

### Post by Duranxl on 2008-09-19
Well the problem has occurred again.
I'm at home right now, and my ubuntu laptop doesn't detect the network through WICD while a 2nd windows laptop right next to it does detect it.

My ubuntu laptop DID detect the network before and it worked fine..but after i rebooted due to a HDD mount related problem the network just wasn't there. (well it was there at first, but it wouldn't connect..then it disappeared)

'iwlist scan' says "No scan results"

What the hell is going on? I just don't understand why such a matured OS can have problems like this. 
Stuff like this is causing me to switch back to windows where i do have a internet.

Any help?

thanks

edit: 30min after i wrote this message my network appeared in WICD again, however just like before i wasn't able to connect. I reboot into windows and voila, works perfectly.....

---

### Post by mykrob on 2008-09-30
next time your connection stops working, run dmesg in the terminal and post the last bit of output as it pertains to wifi.. When my wifi stops working on my intel 3945abg, this is what i get:

```

 366.364061] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  366.364075] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0206 ser 0x0000004E
[  367.357278] iwl3945: Can't stop Rx DMA.
[  367.509199] Registered led device: iwl-phy0:RX
[  367.509241] Registered led device: iwl-phy0:TX

```


I have been using a Belkin USB wifi FD7050, and it works just fine, except it doesnt give proper readings for signal strength.. But at least it keeps the connection alive.

---

### Post by Duranxl on 2008-11-21
The problem has returned once more..I'm currently using windows to write this because ubuntu just won't connect.
It will find every network in the neighborhood, but not my own. Also, many networks are called "hidden" instead of their SSID.
I'm using WICD..none of the drivers make a difference.

I've rebooted, and reset my router but it just doesn't work. I took a 2nd laptop with windows and it works just great..this is seriously starting to irritate me..i keep finding myself choosing windows at the GRUBloader because i can't trust ubuntu on having internet.

Specs:
Intrepid 8.10, fully updated
Intel C2D 7300
2GB RAM
8600M GT

---

### Post by Duranxl on 2008-11-21
So i reinstalled gnome network manager and uninstalled WICD by using a LAN cable.
Still, nothing
Even adding the network manually does nothing

---

### Post by pyles17 on 2008-11-26
I have the 3945 card as well, and I've come to the conclusion that it simply doesn't work. After trying several different solutions, it doesn't connect at all because I don't remember what I did, and therefore can't undo it. The settings are all over the place and I don't know how to reset. 
Whenever I can't sit down and plug into an ethernet cable, it's Windows for me. Pretty much ruined my Kubuntu experience. Oh well.

---

### Post by Duranxl on 2008-11-26
Well, i never changed a thing to any settings. And i actually just fixed the problem by changing my wireless's SSID and encryption from WEP to WPa...but this shouldn't be necessary, i mean come on..like i'm using a alpha version of ubuntu

---

### Post by astadolfo3 on 2008-11-27
Same exact issue with my Vaio VGN 450, Ubuntu 8.10 (same issue for 8.4) with an intel pro/wireless 3945: I can see the networks but when I try to connect the applet tries for about one minute then asks me the WPA password again. This cycle is repeated and the connection is never established.

Interestingly enough, everything work great until 7.10 (included). Apparently on 8.04 the Intel proprietary driver was replaced with an open source one that is causing all these problems. Even with the live CDs, if I boot with the 7.10 or earlier, I can connect without issues. 

Sorry to admit that I've reverted back to Windows (which works without any issues with WiFi) after 8.04: wireless support is vital for me. Since Ubuntu had it working in previous versions, why not use the proprietary driver until a stable open sorce version is available?

I hope a simple fix or an update to the network manager will be available soon.

---

### Post by MacUntu on 2008-11-27
It's not easy to fix things as a lot of users have no problems with the iwl3945 driver (there a tons of hardware combinations).

Best thing you can do is report the bug (either at [https://launchpad.net/](https://launchpad.net/) or directly at [http://www.intellinuxwireless.org/bugzilla/](http://www.intellinuxwireless.org/bugzilla/) ) if not already reported and help finding a fix.

---

### Post by Duranxl on 2008-11-27
Why would the hardware combination be relevant if it's the intel 3945 (driver) causing trouble

---

### Post by MacUntu on 2008-11-27
> **Duranxl said:**
> Why would the hardware combination be relevant if it's the intel 3945 (driver) causing trouble

The driver is the "who" but to fix it you need the "why". Same card, same driver, same OS, same network constellation, different behaviour. Different hardware could be the problem.

---

