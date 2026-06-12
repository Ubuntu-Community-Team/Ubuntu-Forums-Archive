---
title: "Graphics Issue"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by adobrakic on 2009-04-15
My Linux randomly locks up and messes up my screen. I'm not sure why, but I think it's emerald/compiz causing it. 

Here's a small example:
[http://img26.imageshack.us/img26/5974/screenshotowm.png](http://img26.imageshack.us/img26/5974/screenshotowm.png)

Usually what happens is that the whole screen turns like that, and I have to force a shut down. I can't restart xserver by that point.

---

### Post by balaknair on 2009-04-16
I had a similar problem(on Ubuntu Jaunty beta, with an Intel G3500 GMA), where Xserver would lock up and need a hard reset. It would get triggered when I tried using alt-tab or super-tab(app switcher or ring switcher plugins in compiz). What solved the problem for me was disabling the 'widget layer' plug-in in compiz). Do you have widget layer enabled, with screenlets set as widgets? If so, try disabling it and see if the problem still occurs.

Also, could you provide some hardware info(In a terminal type in ***lspci -v*** and post the output here)? And the version of Linux(I see you're using Mint, but which version is it?).
That would help others to get a better idea about the problem you're facing.
Thanks

---

### Post by adobrakic on 2009-04-16
> 
Do you have widget layer enabled, with screenlets set as widgets? If so, try disabling it and see if the problem still occurs.


Actually I did have that, however I disabled screenlets right after I installed them because I noticed an increase in freezing. I still had the widgits plugin in Compiz, but now I've disabled Compiz altogether. I still get issues though, with freezing, just not as bad.

I have Linux Mint 6 64-bit.

```

ado@ado-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f0404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: c0000000-c00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2299
	I/O ports at 18f0 [size=8]
	I/O ports at 18e4 [size=4]
	I/O ports at 18e8 [size=8]
	I/O ports at 18e0 [size=4]
	I/O ports at 18c0 [size=32]
	Memory at f0404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: medium devsel, IRQ 10
	Memory at c0200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: fast devsel, IRQ 19
	Memory at c0000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

09:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at c0100000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

ado@ado-laptop:~$ 

```


This is what happens after I disabled Compiz:
[http://img245.imageshack.us/img245/6085/screenshotr.png](http://img245.imageshack.us/img245/6085/screenshotr.png)

And this:
[http://img22.imageshack.us/img22/8937/screenshothardwaredrive.png](http://img22.imageshack.us/img22/8937/screenshothardwaredrive.png)
(The weird white text with black background)

---

### Post by balaknair on 2009-04-16
Looks like something is seriously messed up with your Xserver settings.

Suggestions:
1) Reinstall the nVidia 180.11 drivers
   (a) Synaptic> find the nvidia driver package(nvidia-glx-180)> Mark for complete removal> reboot> Synaptic> reinstall the driver

   (b) Terminal> sudo apt-get install envyng-gtk---> Then alt+F2> gksudo envyng-gtk and use the envy GUI to uninstall the drivers, reboot, and install the drivers again with envy.

Both (a) and (b) accomplish the same thing.

2) Reconfigure graphics- Select 'recovery mode' from the boot menu when starting the system--> You get a list of options(continue normal boot, repair broken packages, root shell and so on)--> select 'reconfigure graphics'--> restart.

3) install the latest drivers from nVidia(from the nVidia site, not with Synaptic)- the 180.28 drivers actually solved a lot of graphics issues for me with Intrepid. The latest driver package available in the repos is 180.11, whereas the current stable driver is 180.44. Remember however that you will have to reinstall the drivers each time you do a kernel upgrade when using non-repository drivers. I therefore don't recommend this except as a last resort. Be sure to completely uninstall the previous drivers before installing the nVidia-provided drivers(I'd suggest using envy to uninstall safely).

---

### Post by adobrakic on 2009-04-16
Thank you for the response.

I followed your instructions, however I think I ran into some troubles.

I uninstalled 'nvidia-glx-180' fine, but when I rebooted, I had to do it in low graphics mode (understandable). I then reinstalled 'nvidia-glx-180,' and rebooted into recovery mode. There, I could not find "reconfigure graphics," so I used 'xfix' instead, is this the same? 

When I clicked on that, it had a list of options but then it just gave me a message about having a backup somewhere, and then it took me back to the recovery mode menu, from which I went to 'resume boot.' Once I got back on, the 180 driver was installed, but not activated. I had to activate it and restart, is this fine?

Also, would the newest driver (from the nvidia site) be more stable? I wouldn't mind reinstalling them if they work better.

Thanks again

---

### Post by balaknair on 2009-04-16
> **adobrakic said:**
> Thank you for the response.

When I clicked on that, it had a list of options but then it just gave me a message about having a backup somewhere, and then it took me back to the recovery mode menu, from which I went to 'resume boot.' Once I got back on, the 180 driver was installed, but not activated. I had to activate it and restart, is this fine?

Also, would the newest driver (from the nvidia site) be more stable? I wouldn't mind reinstalling them if they work better.

Thanks again
> There, I could not find "reconfigure graphics," so I used 'xfix' instead, is this the same? 

Yes, xfix was what I intended(I think the description says something like 'Reconfigure graphics packages' or 'Repair graphics packages').

> Once I got back on, the 180 driver was installed, but not activated. I had to activate it and restart, is this fine?

I don't think there's any big problem there, so long as it was installed correctly. Do you still get the glitches you were getting earlier?

> Also, would the newest driver (from the nvidia site) be more stable? I wouldn't mind reinstalling them if they work better.


I think you *will* get better performance with the newer drivers. Whether or not the improvement will be worth the effort for you, I cannot say.
Each new release of the drivers fixes bugs in the older versions. And while I haven't tried 180.44(the latest stable release), I did notice significantly better performance with the 180.34(or 37, don't remember for sure) drivers on my 8400GS card on my previous PC. 

On the other hand, if you wait a bit, Ubuntu 9.04 will be released in a week, and it ships with the 180.44 drivers. I'm not sure how long after that the corresponding Mint release(Mint 7?) will be out, but if it's not too long a wait(and if the newly installed drivers work OK for you and you don't get any major errors) I suggest you stick with the current drivers and then upgrade when the next Mint version is released.

---

### Post by balaknair on 2009-04-16
If you do want to go ahead with installing the drivers from the nVidia site, be sure to completely uninstall all the nVidia packages you currently have. If you do want to give it a try, you can find threads with step by step instructions here on the forums, or if you want I can post a detailed howto here(based on the steps I follow, may differ slightly from what you find in other threads). Just ask.

All the best.

---

### Post by adobrakic on 2009-04-16
> 
I don't think there's any big problem there, so long as it was installed correctly. Do you still get the glitches you were getting earlier?


I'm not getting the exact same glitches, but my computer has locked up 3 times since last posting in this thread. Once it happened when I was doing the desktop cube effect, and two other times it just happened randomly. 

> 
On the other hand, if you wait a bit, Ubuntu 9.04 will be released in a week, and it ships with the 180.44 drivers. I'm not sure how long after that the corresponding Mint release(Mint 7?) will be out, but if it's not too long a wait(and if the newly installed drivers work OK for you and you don't get any major errors) I suggest you stick with the current drivers and then upgrade when the next Mint version is released.


Yeah, this sounds good. I'm not all that good with Linux, so I don't want to mess anything else up. I'll just wait for LM 7. If the computer still does it then, I'll consider returning it for a new one.

Thanks a lot again man

--edit--
Nevermind, it just happened again:
[http://img404.imageshack.us/img404/7960/screenshotj.png](http://img404.imageshack.us/img404/7960/screenshotj.png)

I'll just have to see once the new drivers become official, otherwise I'll have to return this laptop.

---

### Post by balaknair on 2009-04-16
OK.

If you decide to try the Nvidia package, feel free to PM me by clicking on my avatar, I'll help in whatever way I can.

In the meantime if I can think of something else that might solve your problem, I'll post it here.

All the best.

---

### Post by adobrakic on 2009-04-16
Okay, sounds good. Linux Mint usually comes out soon after Ubuntu, so I'm not too worried about the wait time.

I'll let you know if I change my mind, though. Thank you

---

### Post by adobrakic on 2009-04-19
After being forced to use Vista (Linux is almost unusable at this point), I started digging at the nvidia website. It seems a lot of people are getting this same issue, and I've seen a lot of people talk about how the Realtek HD driver conflicts with the nvidia driver.

I disabled the Realtek HD driver (no sound now, of course), and it seems to alleviate to issue for right now. Is this plausable for Linux? Do I even use the Realtek HD Driver in Linux?

---

### Post by balaknair on 2009-04-19
Sorry for the delay, I've been trawling the web looking for info about your problem.

> **adobrakic said:**
> After being forced to use Vista (Linux is almost unusable at this point), I started digging at the nvidia website. It seems a lot of people are getting this same issue, and I've seen a lot of people talk about how the Realtek HD driver conflicts with the nvidia driver.

I disabled the Realtek HD driver (no sound now, of course), and it seems to alleviate to issue for right now. Is this plausable for Linux? Do I even use the Realtek HD Driver in Linux?

I'm assuming you disabled Realtek HDA in Vista, am I right?
Your audio device is listed as an Intel 82801 HDA, AFAIK that'd be a Realtek device. But in Linux you'd be using the ALSA drivers' HDA-Intel modules.
To check just type into a terminal
```
lsmod
```

I know of conflicts between nVidia and Realtek drivers on Vista, but this is the first I've heard of it happening on Linux. Did find three matches(about nVidia proprietary drivers nuking the sound, not the other way around as seems to be happening in your case, and not related to Realtek). Since till March 27th I was using an nVidia card with Realtek ALC1200 HDA-Intel audio and proprietary nVidia drivers with no such problems on Ubuntu 8.10, I'm not too sure whether this could be so in your case. I dumped the nVidia card with Jaunty beta as part of a resolve to go open source, switching to the onboard Intel G35 GMA.

In any case, I'd still suggest giving Mint7 a try(Mint comes with the nVidia proprietary drivers enabled by default, right? If so you can try it using the Live CD). I'll try popping my nVidia card back in and giving it a shot at the end of this week, when Ubuntu 9.04 is released(I'll be doing a clean install anyway, got lots of cruft left over from packages I've been testing and kernel patches) and see if there are any issues with nVidia vs Realtek. If I can find something I'll update here and let you know.


**OR**
Maybe you might want to give Ubuntu 9.04 Jaunty Jackalope a shot, the release candidate is now available and is pretty close to the final version. If you have Vista working, maybe do a Wubi install and check if the nVidia graphics(with the 180.44 drivers and 3D) works for you and if it creates conflicts with your audio. That way you can uninstall Wubi once you're done(and decide whether or not to install it on its own partition after trying it out).

Wish you luck for now.

---

### Post by adobrakic on 2009-04-19
Thanks for the suggestions. I'll try the wubi installation of 9.04 and see how that works.

> I'm assuming you disabled Realtek HDA in Vista, am I right?

Yeah, at first it seemed to alleviate most of the problem. However, the nvidia driver started failing again, just like it would with the Realtek HD drivers enabled. 

Also, while it seems the nvidia drivers fail from just about anything, I've found a specific situation that causes it to fail. While I don't know what's actually going on, my driver is guarunteed to fail while it happens. When playing Bioshock, and I go into 'hack' mode (game of pipes, basically), my driver fails after about 3 seconds.

> 
But in Linux you'd be using the ALSA drivers' HDA-Intel modules.


When I went to menu > prefs > sound, the options were all set as "Auto detect." I changed them all to 'Alsa,' and the problem hasn't occured so far.

---

### Post by balaknair on 2009-04-19
In Vista, maybe you should try reinstalling/updating the nVidia drivers. Another major possibility is a hardware error, the graphics card may be getting fried. If your laptop is still under warranty, maybe you should get it checked. I suspect this to be the case since you still get errors/crashes without the Realtek HDA enabled.
nVidia has had a number of recalls due to defects in its mobile GPUs in 2007-08 which caused them to heat up and malfunction. So I'd get a clarification from your laptop vendor ASAP. In many cases a firmware upgrade fixed the problem.

I read up a bit about the nVidia/Realtek issue- seems to be because of a non-standard pin design on nVidia's part which conflicts with other components like audio and modems with older drivers for Vista, but apparently not with the Linux drivers. Will be reading up more about it this coming week.

All the best.

---

### Post by adobrakic on 2009-04-19
Yeah, I've been in contact with Acer since last week now. I also beleive it's simply the hardware malfunctioning. 

They keep telling me to reinstall drivers and stuff, but I'm just going to ask to ship this laptop in and get a new one.

It'd be another thing if the driver kept failing in Vista, however because it's both in Vista and Linux, I think it is the hardware.

Thanks again for all your help

---

### Post by balaknair on 2009-04-19
> **adobrakic said:**
> Yeah, I've been in contact with Acer since last week now. I also beleive it's simply the hardware malfunctioning. 

They keep telling me to reinstall drivers and stuff, but I'm just going to ask to ship this laptop in and get a new one.

It'd be another thing if the driver kept failing in Vista, however because it's both in Vista and Linux, I think it is the hardware.

Thanks again for all your help

Glad to help.

Hope you get things sorted out soon.

All the best.

---

### Post by adobrakic on 2009-04-28
Well, no luck with 32-bit Ubuntu 9.04.

I get the same results:
[http://img411.imageshack.us/img411/5471/screenshotrvt.png](http://img411.imageshack.us/img411/5471/screenshotrvt.png)

At least it doesn't freeze like 64-bit did, I suppose

---

