---
title: "Problem with Screen Size and/or Resolution"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-10
My second PC is an old Toshiba Satellite Pro 4600 running dual-boot Windows 2000 and Xubuntu (installed via wubi).

Ever since I installed Xubuntu the max screen resolution is 800x680, although the machine has always previously been fine at whatever the next size up is (1024x800??).

Does anyone know how I can reset the screen resolution to the proper format?

I've tried looking at the settings for display and nothing higher than 800x680 is an option.

---

### Post by taavikko on 2009-10-10
Wubi in itself is a mess... (as noted by threads containing problems)
Does liveCD have the proper resolution?

What kind of an hardware is running under the hood of toshiba?
```
lspci; lshw -C display
```

And what version of Xubuntu?

---

### Post by Roger Allott on 2009-10-10
> **taavikko said:**
> Wubi in itself is a mess... (as noted by threads containing problems)
Oh. That's a shame. wubi was by far the most convenient and practical method of installing ubuntu on that old machine.

> **taavikko said:**
> Does liveCD have the proper resolution?
Sadly, the CD player in the toshiba no longer works, and it doesn't have 'Boot from USB' in the BIOS options.

> **taavikko said:**
> What kind of an hardware is running under the hood of toshiba?
```
lspci; lshw -C display
```
I can no longer run that command on the Toshiba because I tried upgrading xubuntu 8.10 to 9.04 last night. After a few mishaps where it couldn't upgrade certain stuff, it insisted that I reboot. I did that and the initiation of the OS hung at the same point two times running.

As I didn't have anything too valuable in the xubuntu partition, I booted Windows and uninstalled xubuntu completely.

I've now downloaded xubuntu 9.04 as an .iso file and I'm currently extracting it to a USB drive to see if I can use that somehow. Indeed, I've just noticed that there's a wubi.exe file there!

To answer your question though, Windows tells me that the RAM is 392 MB and the processor is 'x86 Family 6 Model 8 Stepping 6', which I think is another way of saying Pentium III.

Is that spec too poor to run Kubuntu instead of Xubuntu, in your opinion?

> **taavikko said:**
> And what version of Xubuntu?
It was 8.10, now it's nothing, but hopefully I can get it to install 9.04 properly.

---

### Post by Nevart on 2009-10-10
Sorry to state the obvious, because I can see that you clearly have at least some idea of what you're doing, and I don't want you to be offended...

but...

The first thing you should do is find out what video card type is installed in the computer and then download drivers for it, install them, and see if you get more display options.

You also should replace the dodgy CD drive, which is very cheap, or alternatively you could consider using a USB CD drive (but can't boot from that if you can't boot from USB disk *I think* but am not 100% sure on that point).

But replacing the drive is the best idea.  It *is* possible to replace the CD player in a laptop, it is just a lot more work than it would be in a PC.

Updating the video drivers may help.

I have yet to be convinced there is any major advantage in upgrading to 9.04 but it sounds like it is too late for you to roll back anyway.

Also have you tried a BIOS flash?  You might be able to get that old laptop to support USB boot.  Doubt that it is possible, but anything is worth trying when you're at the end of your tether.

---

### Post by Roger Allott on 2009-10-29
> **taavikko said:**
> Wubi in itself is a mess... (as noted by threads containing problems)
Does liveCD have the proper resolution?

What kind of an hardware is running under the hood of toshiba?
```
lspci; lshw -C display
```

And what version of Xubuntu?

I'd like to reignite this thread because I have now installed xubuntu karmic on the Toshiba - and not by wubi but as a puckka, kosher, full-strength expresso install, scrapping Windows 2000 completely in the process.

But I still have the problem of screen resolution being no more than 800x600.

OK, so to answer the question of what's under the hood:

```
$ lspci; -C display
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
-C: command not found
```

---

### Post by Roger Allott on 2009-10-29
On doing a bit of searching around this and other forums, it seems that the problem I've got is not in the slightest bit rare.

An often reported solution is:
```
sudo displayconfig-gtk
```
and resetting the graphics card to "Trident Cyber Blade" (or something like that). A quick reboot and the screen works properly at 1024x768.

I've just tried doing exactly that and got this as my response:
```
sudo: displayconfig-gtk: command not found
```

which just makes me want to smash my head against the nearest brick wall!!!

PLEASE can someone help me?????

---

### Post by Roger Allott on 2009-10-30
I've found another option, which was posted back in December 2005:

> **[Re: Can't edit xorg.conf Do i need root or what?!?!]("http://ubuntuforums.org/showpost.php?p=593980&postcount=3")**
all sensible config files are owned by root. that's a basic security feauture. open a terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

Then enter your user password, and a text based config dialog will guide you.

That would be rather nice I think, but when I type that into a terminal window in xubuntu 9.10 I get .......
..... absolutely bloody nothing except a return of the $ prompt.


AAAAGGGGGGGGHHHHHHHHH!!!!!!!

---

### Post by Roger Allott on 2009-10-31
It would seem that I incorrectly typed the command to get info about my hardware, so here's the output of lshw -C display:

```
$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/XP
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 63
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=8
       resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9ffffff memory:f7ff8000-f7ffffff memory:20000000-2000ffff(prefetchable)
```

The line that worries me is:
```
  *-display UNCLAIMED
```
So how do I get my display claimed??

---

### Post by tmcmack on 2009-10-31
Same problem here, on a Toshiba Satellite A25 laptop probably similar to Roger's. I installed fresh from the Koala CD, complete with format to ext4, but kept my old home partition. The max resolution is 800x600 when prior versions of ubuntu allowed me to take advantage of the monitor's max 1024x768. Whether I run directly from the hard drive or from the live CD, the screen shows the 800x600 window in the middle of the screen, with 1.5 inches of black bars around it.

Lots of solutions out there for prior versions of Ubuntu, but from what I read, it seems that Koala deals with xorg differently. I don't even have an xorg.conf file, and many solutions involve editing that file.

Should my next step be to look for video drivers? I don't recall having to do that in prior versions. Not sure what my next step should be, given these changes in the system setup for this version.

Thanks for your help, all.

```
$ lspci; lshw -C display
00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=8
       resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9ffffff memory:f7ff8000-f7ffffff memory:58000000-5800ffff(prefetchable)
```

---

### Post by tmcmack on 2009-11-01
Not sure if this is the right way, but here's how I fixed this problem:

1. Started the system in recovery mode from the boot loader and then went to a root command prompt.
2. Ran the command "xorg -configure", which generated an xorg.conf file at /root/xorg.conf.new
3. Moved that file to /etc/X11/xorg.conf
4. Fiddled with the settings in that file as described on this page:
[http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/](http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/)
5. Restarted X with "sudo /etc/init.d/gdm restart"

Other relevant threads are [here]("http://ubuntuforums.org/showthread.php?t=1299246") and [here]("http://ubuntuforums.org/showthread.php?t=1275521").

---

### Post by Roger Allott on 2009-11-01
> **tmcmack said:**
> Not sure if this is the right way, but here's how I fixed this problem:

1. Started the system in recovery mode from the boot loader and then went to a root command prompt.
2. Ran the command "xorg -configure", which generated an xorg.conf file at /root/xorg.conf.new
3. Moved that file to /etc/X11/xorg.conf
4. Fiddled with the settings in that file as described on this page:
[http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/](http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/)
5. Restarted X with "sudo /etc/init.d/gdm restart"

Other relevant threads are [here]("http://ubuntuforums.org/showthread.php?t=1299246") and [here]("http://ubuntuforums.org/showthread.php?t=1275521").

Yes, I did it in a very similar way, as described in [this thread]("http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283").

---

