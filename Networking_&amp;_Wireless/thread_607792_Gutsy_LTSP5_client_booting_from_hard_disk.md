---
title: "Gutsy LTSP5 client booting from hard disk?"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by drink on 2007-11-09
I have ventured into the least well-documented portion of [Ed]Ubuntu - LTSP. Practically every document on booting says you can boot from a hard disk, but none of them tell you how to do it. Why? As far as I can tell, because no one actually has figured out how to do it :P

The whole world is focused on PXE booting, but if you have something without it then what do you do? I have an iOpener I want to use as a LTSP client. There's a couple readmes out there on the topic but none of them have helped me yet, and none of them apply to LTSP5 anyway.

I tried loading the kernel and initrd from the tftpboot directory. No joy. Just getting the ltsp-build script to work in the first place was a huge PITA for me, a modem user. I don't want automatic security updates and I absolutely must use my local mirror. Both require hackery. I'm not sure who is actually served by forcing the user to download from the internet on install, but anyway.

I have rtl8150 USB ethernet and have no other options. I cannot PXE boot in any way as a result, at least not without perhaps using a linux kernel to do it somehow. Etherboot doesn't appear to support USB, or at least, faq-o-matic doesn't (I hear there was a patch once to support USB on Etherboot, but I couldn't find any recent references.)

I have a 16MB SunDisk DiskOnChip to work with. I can load a boot image into it from Linux or DOS installed to a 2GB laptop drive I have lying around. I have installed the CLI-only gutsy and the xorg server plus the dependencies for same so that I have something to work with, but the system has only 64MB so just booting is a long process.

Formerly I was booting this thing from Midori4iOpener (M4I) 2.3pre1, but the original site has gone away and I can't seem to find that image any more. It was a linux 2.4(.20?) with Opera 5 (yuck) and my driver. This was sufficient to get up and run X -query, although it had only ssh1 etc. I really wanted to move to LTSP and I have finally got a LTSP setup installed on a machine here, but now I can't get my client to function. I have doubts about the usefulness of LTSP5 on such a low-end machine (Looks like LTSP, like everything else, is abandoning low-end hardware now - what was the point again?) but I still want to try to be current.

Anyway, has anyone actually gotten hard disk booting of the LTSP kernel to work? Can anyone give me pointers on producing an initrd that will contain my driver? The tools are themselves built upon poorly documented tools....

---

### Post by SpiritIsReality on 2007-11-09
howdy 
While I'm readin' your post, could you have a look at some of the links at the bottom of this page? [http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp)
I think at the UbuntuLTSP page there's one that hints at installing the boot image to harddrive. I'll have to find it.
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)
The solutions to your network are beyond my present grasp of LTSP.
trails

---

### Post by drink on 2007-11-09
> **SpiritIsReality said:**
> howdy 
While I'm readin' your post, could you have a look at some of the links at the bottom of this page? 

OK so I read (or at least skimmed, some of each) all of that stuff, and again there are only hints of how to get where I want to go, no actual answers. And everyone who presents a "solution" has done precisely the same thing - use an etherboot floppy. As lovely as PXE would be (and it would be, believe me) I have a USB rtl8150 so as far as I can tell etherboot can not help me, and rom-o-matic certainly can not (I've been there of course.)

I can put whatever PC OS on a disk or cdrom and connect via my wizztronics all-in-one adapter for iopener. But really I only want to use that to bootstrap and load something into the 16MB. I wanted LTSP, but right now I'm working on a solution using freedos and loadlin to boot a totally custom autoconfiguring kernel and initrd. I understand there's some way to load linux from linux (and I've definitely used something like that, because I used to have a cobalt raq4 and that's how its bootloader operates) so perhaps I'll work out a way to load LTSP from there.

Optimally I want to end up with a kernel and initrd, and with enough libraries and whatnot to load a decent X server right on board, and the ability to netboot. I'd love to use Xorg but I'd be happy enough with XFree, which might produce a smaller server. I imagine I'd have a dhcp client (typ. pump in these images) and busybox. I'm hoping to use the existing tools (e.g. mkinitrd) to accomplish this so I don't have to do anything hard. I have some guides on subjects like this but none of them are very cookbookish either, which is what I was hoping for.

---

