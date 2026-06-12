---
title: "Computer lags when I want to login!"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-17
Hello guys, so here is the problem: Whenever I go away from my computer (say 30 minutes or more) and leave Ubuntu running (in most cases I would be downloading something, but sometimes you just need to get some fresh air!), so when I come back, the screen would be off, and when I move the mouse or press any key on the keyboard, my screen saver appears but frozen, and I can't type in my password or do anything so I have to shutdown my computer by force, and then boot it up again, any solutions for the problem!!!?

---

### Post by RichardLinx on 2011-08-17
Can you post the output of:

```
lspci
```

Sounds like a kernel panic. I don't know how to fix it, but knowing your hardware might be of some help.

What version of Ubuntu are you using? Are you using open or closed drivers for anything? When did this problem start?

---

### Post by RichardLinx on 2011-08-17
This might fix it:
> 
Problem: Sync to VBlank

VBlank synchronization is an optimization technique that balances the output rate of your graphics card with the rate that your monitor displays images on the screen. Your monitor's refresh rate -- also called the vertical blanking interval (VBlank) -- is the maximum speed your monitor can present images. If your graphics card renders faster than this rate, the extra images are rendered for naught, as you'll never actually see them. So if your monitor's VBlank is 60 Hz, and your graphics card is rendering 1000 frames-per-second, then 940 frames are getting drawn for no purpose. So theory synchronizing the two makes a lot of sense.

HOWEVER, things are not so simple, and vblank syncing can actually make performance worse. For a deeper discussion, see [http://www.tweakguides.com/Graphics_9.html](http://www.tweakguides.com/Graphics_9.html)

To turn off vblank sync, use any of the three methods:

1. Setting vblank using compizconfig-settings-manager: Go to System->Preferences-> Compiz config settings manager -> general options -> Display settings-> Sync to VBlank. Turn it to 'off'.

2. From the compiz gconf configuration:

    sync_to_vblank = false

3. Via driconf: 'Synchronization with vertical refresh (swap intervals)' -> set to 'Never synchronize with vertical refresh'.

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:_Sync_to_VBlank](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:_Sync_to_VBlank)

---

### Post by the-new-x on 2011-08-17
Here is the output of the command:

tatah@Satellite-A505:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
04:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
tatah@Satellite-A505:~$ 



And no I do not think that the second suggestion is the problem, I have only installed Ubuntu around 10 days ago, and this problem have been happening since then. (My laptop's monitor worked just fine under the 60 Hz refresh rate, when I first came to Ubuntu, I played with some settings, one of those is the refresh rate, it was 30 Hz so I changed it to 60 Hz.)
Note that I can see my mouse and I can move it freely around the screen!

---

### Post by the-new-x on 2011-08-17
I am using Ubuntu 11.04 natty x64, with the unity layout.
And also, I can't see the display settings that you wrote about in the compiz config settings manager!

---

