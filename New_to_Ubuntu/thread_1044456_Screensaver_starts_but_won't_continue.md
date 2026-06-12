---
title: "Screensaver starts but won't continue"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by -kg- on 2009-01-19
My problem is that, when I activate the screensaver, no matter what screensaver I select, after the wait period the screen will start to darken as if the screensaver is activating, then once it gets completely dark, it will come back out of screensaver mode.  If I let it go, it will continually repeat this process.

I have searched back even into the archives and there was only one thread with a problem even remotely similar:

[http://ubuntuforums.org/showthread.php?t=903992&highlight=screensaver+problem]("http://ubuntuforums.org/showthread.php?t=903992&highlight=screensaver+problem")

This thread was from Aug/Sep of last year and was marked "solved," having been resolved thusly:

> I have both compiz-fusion and cairo-dock installed...

...Apparently, it has something to do with Cairo-Dock. When I take it out of the startup menu to start automatically, it solves the problem.

I don't have Cairo-Dock installed, to my knowledge (How would I check this?).  Also, AFAIK, this has always happened on my laptop.  It's one of the problems that weren't that important to resolve.

I am running BOINC projects on this computer, and I thought that might be it, but I'm running BOINC on my desktop, too (64 bit on the desktop), and the screensaver works fine on it.

Any idea what I should check and how to resolve this issue would be much appreciated.

---

### Post by Terl on 2009-01-19
Is the laptop on battery or ac when this happens?

As for cairo-dock you would have had to install it, so if you do not recall doing that you probably do not have it.  You could try typing "cairo-dock" (without the quotes) in terminal and see what it says.

---

### Post by -kg- on 2009-01-19
> **Terl said:**
> Is the laptop on battery or ac when this happens?

As for cairo-dock you would have had to install it, so if you do not recall doing that you probably do not have it.  You could try typing "cairo-dock" (without the quotes) in terminal and see what it says.

I don't recall installing it but tried the command in terminal anyway.  "Command not found"  The laptop is on ac power (almost constantly, in fact).

---

### Post by Terl on 2009-01-19
Does it do this no matter what you may be running?  I am not sure what you mean by "BOINC projects".  Does it ever go into screensaver, like when you have it doing nothing?  This may help figure it out.

What brand laptop is it?

---

### Post by -kg- on 2009-01-20
> **Terl said:**
> Does it do this no matter what you may be running?  I am not sure what you mean by "BOINC projects".  Does it ever go into screensaver, like when you have it doing nothing?  This may help figure it out.

What brand laptop is it?

Yes, it does this no matter what is running.  I've suspended the BOINC Manager and client with no effect at all.  And, as I said, I have it running on my desktop as well, with no effect on it's screensaver. The screen starts darkening after the time delay I set, get's almost black as if the screensaver is about to kick in, then pops back out of screensaver mode.

[BOINC]("http://boinc.berkeley.edu/") is the Berkeley Open Infrastructure for Network Computing.  Included are such things as SETI@Home, which I've been doing for years; various "Folding@Home" type projects; Climatology computations; and other various projects that require a huge amount of computing power.  Work units are distributed to personal computers world-wide.

This is a Toshiba Satellite A135-S4487 w/ an Intel Duo-Core T5500 processor, 2 GB RAM, 240 GB HD space in two physical hard drives, and came with Vista, with which I dual boot Ubuntu Hardy 8.04 i386.

---

### Post by Terl on 2009-01-20
Do you have graphics drivers installed on the laptop?  On my laptop (a Dell) the screen dims before the screensaver kicks in and the the saver starts.  I wonder if you are having issues with the graphics card that is disallowing the screensaver to start.

---

### Post by -kg- on 2009-01-20
I have no proprietary drivers installed.  The following is the results of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

---

### Post by -kg- on 2009-01-21
Bump

Sorry it's so long between posts.  I have a lot going on right now.

---

### Post by bchecca1 on 2009-01-23
I am having the same issue... I just started to use a screen saver, and this same thing is happening.

I'm running a Dell Optiplex 150 using 8.10.

Any ideas as to what's going on?

---

### Post by misterupsidedown on 2009-02-18
not sure if this helps, but i had some luck messing with the power management settings (system/preferences/power management - acpower tab).  unchecked the "dim display when idle" box and it worked. i've since dropped the screensaver in lieu of just putting the display to sleep.

---

### Post by Razmear on 2009-03-13
I found this thread because I was having the same issue on my desktop. 
I managed to finally fix it by uninstalling gnome-screensaver and installing xscreensaver thru the synaptic package manager. 

Disabling blanking and ever uninstalling the power management services made no difference, but xscreensaver seems to have done the trick, and I have customization of the savers now. 

eb

---

