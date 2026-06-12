---
title: "Nvidia 8400 GS not working"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by shinjimx on 2010-03-17
Hi everybody. I have this little weird problem:

Recently I made a small machine with an intel mobo D945GCLF (atom proc 1.6 ghz, everything integrated), 2 GB RAM, 2 HDD (80 GB for OS, 1.5 TB for storage). Everything was fine, I used an Ubuntu live CD to test if it booted, then installed Win7 RC to test media center capabilities. Later I added an EVGA Geforce 8400 GS PCI to make it a bit more powerful. Again, everything was fine.
Then, as probably you know, Win7 RC is going down, so I decided to install Mythbuntu to keep it a media center... it wouldn't boot. Neither with Ubuntu 9.10, Fedora 12, OpenSuse 11, Xubuntu 9.10... last night I thought of taking off the video card and boot with the integrated graphics and voila! everything was fine, I could install Xubuntu without a problem, updated, then I thought of putting again the card... no luck, there was no signal in the monitor after the intel splash screen. First it was connected via DVI, changed the port to VGA (the card has both ports) and could see the kernel selection screen, but after that again there was no signal.

Anyone has had this problem or a similar one?

In advance, thanks for the help.

Saludos

---

### Post by coffeecat on 2010-03-17
> **shinjimx said:**
> Anyone has had this problem or a similar one?


Not quite, but one thought. The machine I'm posting from I've fitted a GeForce 8400GS PCIe (not PCI) card, but it also has onboard nvidia graphics (less capable chipset). I didn't have the booting up problems that you did, but I did have some weird issues when I installed the proprietary driver. Long story short - the BIOS was not automatically disabling the onboard graphics with the PCIe card fitted. The entry in the BIOS to disable the graphics was not well worded - it took me some time to find it and work out what it meant - but once I'd disabled the onboard graphics everything worked just fine.

This took me by surprise. I had thought that the default was to autodisable onboard graphics when the BIOS detected another graphics device. This was certainly true of several other motherboards I have used.

So - check the BIOS. See if there is somewhere to disable onboard graphics.

---

### Post by jim Kane on 2010-03-17
> **shinjimx said:**
> Hi everybody. I have this little weird problem:

. last night I thought of taking off the video card and boot with the integrated graphics and voila! everything was fine, I could install Xubuntu without a problem, updated, then I thought of putting again the card...

Saludos

                                       Have you checked the bios


    [LEFT]Mini Card>> Enables or disables the PCI Express x1 minicard slot.


jk
[/LEFT]

---

### Post by shinjimx on 2010-03-18
Well, I checked the BIOS, change the video config and select te PCI external graphics, same result, again no video signal. After a while I pressed a key and the system send this message:

[HTML]mount: mounting /dev/disk/by-uuid/01d3022a-91a5-4b99-924d-28240f02a20b on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/HTML]

After that, I turned off the pc, took off the card, and everything was normal... I'm really puzzled with this. A similar problem happened with my laptop with ubuntu 9.04 (about august '09), I waited a bit for the alpha of 9.10 and it booted correctly (then installed the stable version of 9.10 on said laptop). Did the same for this problem with the 10.04 alpha but didn't work.

Well, I'll keep on testing. Thanx for the help.

---

### Post by Agerak on 2010-06-23
bump.

Same issue, forced to use on-board video.  There are multiple posts, same motherboard in 3, one was a single core ATOM variant.  All have had issues when attempting to boot to the external graphics card.  Once you go back to the on-board, all issues are gone.  This seems to be a very common issue and since the appeal of a small, efficient ubuntu system would be commonly based on this type of solution, I think it deserves some serious attention.

I would like to know of ANYONE who has managed to get an ATOM based system with PCI graphics functioning.  I have yet to see one.

---

### Post by mojo6911 on 2010-10-19
This should fix it:

[http://ubuntuforums.org/showpost.php?p=1252865&postcount=2](http://ubuntuforums.org/showpost.php?p=1252865&postcount=2)

---

