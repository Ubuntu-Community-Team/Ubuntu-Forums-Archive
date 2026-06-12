---
title: "What video driver / software should I have? (ATI)"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Cooker on 2011-02-12
I really F'ed up my display. I tried to install ATI's Radeon driver on my laptop (Acer 4420 w/ ATI Radeon xpress 1250) and failed horribly. Tried uninstalling the driver and things took a turn for the worse, boot up only gave me the terminal (yikkes).  Got my display back fortunately but now I'm having trouble with my compiz not working AND going fullscreen in flash videos.
I should have left things the way they were before, everything was working perfectly fine. I'm such a dumbass.

First question; Is all this software necessary? 

[IMG]http://i926.photobucket.com/albums/ad106/dpcookson/Screenshot-1.png[/IMG]

Second question; How do I get back to where I started?

---

### Post by clhsharky on 2011-02-13
Cooker

ATI Radeon Open Source Stack driver installed by default is correct for your ATI Radeon xpress 1250 chip.


1 - All of those are default install, just leave them.

2 - Typically, the following manual commands will properly uninstall -fglrx: 
In terminal copy/paste one line at a time, then enter.
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
  sudo dpkg-reconfigure xserver-xorg
```
If you want desktop effects (compiz or KDE) you'll need the glx module loaded. This will not work even after purging fglrx since a hanging libglx.so file is left around. Both fglrx and xserver-xorg-core provide this file so to replace it with the correct version you'll need to reinstall xserver-xorg-core as well. 
```
sudo apt-get install --reinstall xserver-xorg-core
```
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

As for flash in fullscreen try these commands:
```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```
Restart the browser.

If that doesn't work, then right-click the flash video, select "Settings", then untick the option "Enable hardware acceleration".
[http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)


Sharky

---

### Post by jerrrys on 2011-02-13
you shouldn't be looking for drivers in the software center.  instead go to

system>administration>hardware drivers

with any luck this will tell you which driver to download and fix your problem

---

### Post by clhsharky on 2011-02-13
> ATI Radeon Open Source Stack driver installed by default is correct for your ATI Radeon xpress 1250 chip.
There are no proprietary drivers for this chip in Karmic,Lucid or Maverick.

Sharky

---

### Post by Cooker on 2011-02-13
clhsharky,

I tried the codes you listed but still seem to have the same problems. I'm pretty sure I already got rid of fglrx but used the codes anyways. It said no fglrx was installed. Went through with the rest of the codes you suggested just to be 100%. 

The codes for adobe didn't work either but unselecting hardware acceleration did, thank you.

And I almost totally forgot, after closing then reopening my laptops lid the screen stays black and won't come out of suspend.

Not sure if this matters either but this is what I get when I type in  lspci;

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
```

---

### Post by Mark Phelps on 2011-02-14
> **jerrrys said:**
> ...instead go to 
system>administration>hardware drivers

with any luck this will tell you which driver to download and fix your problem

Actually, it won't ... because there are no restricted drivers for that card since Ubuntu 8.10.

---

### Post by Cooker on 2011-02-14
Anyone able to help out?

---

### Post by 3rdalbum on 2011-02-14
> **Cooker said:**
> Anyone able to help out?

Yes. Just stick with the default driver; it's the only one that can run your GPU.

---

### Post by Cooker on 2011-02-15
Maybe I'm just not making myself clear enough here.

BEFORE any of this my computer worked almost flawless aside from the external monitor out not working properly which I'm now assuming is a hardware problem not software.
 
I attempted to install ATI's Catalyst driver and Control Center and had catastrophic results. I'm an idiot, that's fair enough.

I somehow(don't remember how exactly) got my display back good enough to get Ubuntu to load up completely but still had Catalyst Control Center in my System/Preferences. I BELIEVE that it is now gone too but I am unsure how to check.

My system files seem to be littered with fglrx, which I THOUGHT were removed entirely but obviously were not. Now I don't know how to safely remove them without more catastrophic events.

I used to be able to enable "extra" visual effects but cannot any more.

I have compiz and compiz config settings manager but any settings I apply there don't do anything whereas they worked before.

My computer used to come out of suspend problem free but now seems like it wants to (powers back up, backlight comes on) but the screen stays black.

I am hoping someone here can help me get my computer back to normal here, I think something is really messed up, even though it kinda works, it's ticking me off enough that I've contemplated wiping the whole hard drive and re-installing Ubuntu (not really wanting to but....).

The site that I followed instructions on installation is here if that helps; [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

Any help is greatly appreciated.

---

### Post by el_koraco on 2011-02-15
had similar problems with an emachines 442 Radeon HD4250 proprietary flgrx driver. messed up my splash screen, made compiz effects unsustainable, caused longer boot times, as well as effecting overall system performance. tried to purge it with the commands that sharky posted, but got nowhere. got booted to bash three or four times. finally decided it wasn't worth the hasstle, so i did a fresh install, ignored the piece of crap, and it's been smooth sailing ever since. 

not overtly helpful, i know, but at least you know you're not the first one to find yourself in the same mess.

---

### Post by hansolo4949 on 2011-02-15
Just stick with what works, and do not try to get better performance out of the card. There is just a bit too much risk when it comes to trying to install video drivers. As long as the default worked, just reinstall Ubuntu if you just upgraded (easiest solution), take a deep breath, and stick with the default. Enjoy Ubuntu!

---

### Post by Mark Phelps on 2011-02-15
Unfortunately, it's not a simple matter to clean up after an fglrx driver install -- as you're finding out.

And, suspend/hibernate can be adversely affected by video drivers -- which is probably why they don't work anymore.

Hate to say it, but a fresh, clean install is probably going to be needed to get things back to working order.

In the future, if you want to experiment with drivers, strongly suggest you look into using CloneZilla to image off your current setup.  The ten minutes it takes to do the backup, plus another ten if you have to restore, saves HOURS of messing around if things get really trashed.

---

### Post by Cooker on 2011-02-16
Thanks for the guidance, I'm still fairly new with Ubuntu and I was just wondering if there was some easier way around it but I think I'll just bite the bullet on this one and do a fresh install. It's probably the safest route and a sure bet that flgrx will be annihilated.

---

