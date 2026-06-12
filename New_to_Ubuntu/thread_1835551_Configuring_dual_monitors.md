---
title: "Configuring dual monitors"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-29
I recently bought a new Dell Optiplex 790 and installed ubuntu 11.04 on it. I bought it with a 23" Dell monitor, and everything works fine. However, today I tried to plug in a second monitor that I had sitting around and I can't get the dual display to work correctly. 

Initially when I started up the computer, it started with the same image on both monitors. I opened up Monitor Preferences and unchecked 'same image in all monitors' and then tried to drag the monitors into the arrangement that I wanted, but when I click apply I get the error message

> The selected configuration for displays could not be applied.

requested position/size for CRTC 147 is outside the allowed limit: position = (1920,0), size=(1280,1024), MAXIMUM=(1920,1920)


The second monitor is an older and smaller monitor, but it doesn't seem to me that it should make much of a difference but maybe it does. I have the resolution set on the 23" monitor to be 1920x1080, and on the smaller monitor to be 1280x1024. 

Also, just in case this has something to do with my graphics card, I'll give that information. The graphics card in the computer was listed in my order as

 512MB AMD RADEON HD 6350 (2 DVI), Low Profile

When I use lspci -v to get the detailed information on my card I get
```

01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 2126
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e1420000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at e1400000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

```

---

### Post by themusicalduck on 2011-08-29
I use Nvidia instead of ATI, but Nvidia has its own software for configuring dual-monitors. I think ATI uses its own software too, called the Catalyst Control Centre. See if you can find it somewhere installed on your system.

This would only work if you installed the proprietary drivers though.

---

### Post by peterson43 on 2011-08-29
Also, one other thing that is funny. When the monitors are configured so that the same image is displayed on both machines, the resolution is set to be 1280x1024 (the correct resolution on the smaller screen). 

My graphics card only came with a single DVI out port, but it came with a splitter cable that had the two extensions labelled '1' and '2.' I assumed that by plugging the large monitor into the '1' would make it the default primary monitor.

---

### Post by peterson43 on 2011-08-29
I found the Catalyst Control Center, and that fixed some of the problems. I was able to configure my screens side-by-side. The only issue is that the smaller screen is recognized as the primary screen instead of the larger screen. Thus the Launcher in the Unity desktop appears on the smaller screen instead of the larger screen where I want it. 

I can't figure out any way to change this in the Catalyst Control Center. Also, the other funny thing is that when I get to the login screen, it appears on the big monitor. Thus it appears that the large monitor is acting like the primary monitor when I'm logging in, but the small monitor becomes the primary one once I get logged in. 

Any thoughts on how to fix this?

---

### Post by Johnb0y on 2011-08-29
swap splitter around and "tweak" in control centre? possibly?

---

### Post by peterson43 on 2011-08-30
I was able to get the Catalyst Control Center to recognize the large monitor as #1. I started the computer up with only the large monitor plugged in. Then, while the computer was running I plugged in the second screen so that it would register as #2. After setting up the dual display in the Catalyst Control Center I then restarted the computer to have things take effect. When I turned the computer back on the second screen didn't register right away, but it did after I visited the Catalyst Control Center one more time to turn on the dual display. 

However, even though the large monitor is registered as #1 and is configured to be on the left, the Launcher is still located on the smaller monitor. How do I fix this?

---

### Post by peterson43 on 2011-08-30
I'll mark this thread as 'solved' since using Catalyst Control Center fixed my initial problem of not being able to display the screens side-by-side. 

I'll post my new problem of where the launcher menu appears in a new thread.

---

### Post by PGScooter on 2011-09-10
peterson43,

I am having trouble finding the Catalyst Control Center. I have the package installed (fglrx-amdcccle) but don't know what to do after that. Any ideas? Thanks

---

### Post by peterson43 on 2011-09-12
> **PGScooter said:**
> peterson43,

I am having trouble finding the Catalyst Control Center. I have the package installed (fglrx-amdcccle) but don't know what to do after that. Any ideas? Thanks

The Catalyst Control Center should be in System Settings. In Ubuntu 11.04 this is found on the button on the top right of the screen that also has options for log out and shut down. 

If you can't find it in system settings, you can run it from a terminal by typing 
```
sudo amdcccle
``` 

If it still doesn't work then there must be some package dependencies missing.

---

### Post by PGScooter on 2011-09-14
Thanks, I'm using 11.10 and couldn't find it in the menu but the command worked fine and I was able to get things set up. Thanks for the explanation

---

