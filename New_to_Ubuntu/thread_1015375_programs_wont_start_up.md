---
title: "programs wont start up"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by PsYcHoTiC_MaDmAn on 2008-12-18
had an old XP computer that wasn't working (kept rebooting, kept giving the BSOD when I attempted to re-install)so desided to chuck ubuntu on it.

downloaded it off the site(ubuntu-8.10-desktop-i386.iso), burned the ISO to disk, but none of the computers would do anything with it (either from boot, or when in XP) so downloaded UNetbootin, and ran that. the first PC wouldn't boot from USB, so removed the hard disk from the main PC, and shoved the old PC hard disk in. and booted from the USB, then installed.

worked fine on the first machine, and I was able to connect to the web, and the various applications worked. however, moving the HD over to the other machine it boots up, but then doesn't allow programs to start. 

as more of an explanation, it opens a box on the taskbar stating "starting ..." (eg  "starting firefox") then that closes and nothing happens.

1st PC (working XP one), 512mb PC3200 RAM, AMD athlon 64 3200+ (1.9Ghz) 160gb hard disk

2nd PC 256mb PC2100 RAM, AMD athlon 1.2Ghz, 20gb Seagate hard drive

and as I type this it finally starts working, but I've rebooted the machine 10-15 times to get this far

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-18
and just after I posted that, the PC rebooted without me doing anything

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-18
dont know if its a symptom or not, but the scroll lock and caps lock indicators are flashing. 

I'm in the process of downloading xubuntu, and hopefully that with its lower requirements will run properly

---

### Post by g0rd99 on 2008-12-18
> **PsYcHoTiC_MaDmAn said:**
> had an old XP computer that wasn't working (kept rebooting, kept giving the BSOD when I attempted to re-install)so desided to chuck ubuntu on it.

downloaded it off the site(ubuntu-8.10-desktop-i386.iso), burned the ISO to disk, but none of the computers would do anything with it (either from boot, or when in XP) so downloaded UNetbootin, and ran that. the first PC wouldn't boot from USB, so removed the hard disk from the main PC, and shoved the old PC hard disk in. and booted from the USB, then installed.

worked fine on the first machine, and I was able to connect to the web, and the various applications worked. however, moving the HD over to the other machine it boots up, but then doesn't allow programs to start. 

as more of an explanation, it opens a box on the taskbar stating "starting ..." (eg  "starting firefox") then that closes and nothing happens.

1st PC (working XP one), 512mb PC3200 RAM, AMD athlon 64 3200+ (1.9Ghz) 160gb hard disk

2nd PC 256mb PC2100 RAM, AMD athlon 1.2Ghz, 20gb Seagate hard drive

and as I type this it finally starts working, but I've rebooted the machine 10-15 times to get this far

I don't like your chances of the same disk working well off different hardware. Poor Ubuntu must be thorouly confused.
I must ask a silly question: did you adjust your bios to boot from CD?
Gord

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-19
> **g0rd99 said:**
> I don't like your chances of the same disk working well off different hardware. Poor Ubuntu must be thorouly confused.
I must ask a silly question: did you adjust your bios to boot from CD?
Gord

yes. set to boot of cd, but none of the computers would read the disk. the one computer would boot off USB, so used that instead.

what puzzles me is more the haphazardness of it. sometimes it boots, other times it doesnt. sometimes programs start, other times they dont.

I swapped ubuntu for xubuntu as that should be better on a lower spec machine. but its still not running great. 

I've gotten both ubuntu and xubuntu to connect to the web a few times. basically all I want the other PC for is anther web access, as |I type this its currently running, but its taken a good 10 reboots to get there

---

### Post by scorchgeek on 2008-12-19
Select the "Integrity Check" or "Verify" option from the CD boot menu to make sure your CD burner didn't screw up. If there's something wrong, just reburn it.

---

### Post by Kellemora on 2008-12-19
Hi PM

I've had to do that with a couple of older machines myself that don't even have CD's in them.

One only has a 10mb LAN connection too.

I honestly installed Hardy on a 4 gig drive in an old Doze98 machine, by first putting the drive into a newer machine to load Hardy onto the drive.

Naturally the drivers were wrong, but amazingly, it figured it out on it's own and replaced the drivers with the right ones.  Then I dropped a 10 gig drive in there for /home and use it as my test machine.  It got all the downloads before I would put them on the good machines.  It's where I try hair-brained stunts first too, hi hi........

I've loaded a few kids games onto it from the repositories, so the kids have something to play on when stuck in my office for a few hours.  Keeps them outta my hair too, and from messing with stuff.

TTUL
Gary

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-20
> **scorchgeek said:**
> Select the "Integrity Check" or "Verify" option from the CD boot menu to make sure your CD burner didn't screw up. If there's something wrong, just reburn it.

verified both on the PC I burned the dvd on, and used that function on the other PC that I was trying to install onto. 

both came back as that the CD was free from errors

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
An update on where things are. (hence the repeat on all 3 other threads I started otherwise)

tried installing XP pro afterwards, and had a page file error, so no luck then. 

however I recieved the RAM I'd ordered for the other pc (the one I'm typing on) so transferred the 512mb stick from the 1 machine to the other. 

attempted to boot off the CD, but had no luck again, no idea what the problem was (got through the choose language etc, and when I tried install it just froze up). so transferred the hard disk to the other machine (this 1 again) reformatted it, (Ext3) and installed it via USB stick (incidently, made a mistake with unetbootin, setting it to xubuntu, when i didnt realise it was the ubuntu I had selected) and installed all the updates. 

having done that I then transferred the hard disk back to the other machines, (with a degree of worry that what had previously happened would reoccur) and it booted up fine.

I've had it running for several hours, downloaded and installed flash player, and its running perfectly. 

so works fine with 512mb of RAM, but not so with only 256 (that goes for both ubuntu and xubuntu)

---

