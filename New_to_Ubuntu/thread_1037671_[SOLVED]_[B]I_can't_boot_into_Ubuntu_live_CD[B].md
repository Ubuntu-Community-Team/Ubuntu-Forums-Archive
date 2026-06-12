---
title: "[SOLVED] [B]I can't boot into Ubuntu live CD[/B]"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by trigity on 2009-01-12
**Can't run CD because it say's autorun error. I'm trying to fix my MBR and do some other work in the shell and I need to use the terminal on the CD**

---

### Post by aesis05401 on 2009-01-12
Can you tell me where you are when the autorun error pops up?

There are a couple Launchpad bugs I have seen related to autorun errors, but they are distinct, and IIRC the ones I knew of have been closed.

Is your disc recent?

---

### Post by cybergrunt on 2009-01-12
Yes I had real issues with this and as unlikely as it seems my optical drive had issues. I also have problems with booting live cds on my Dell Precision M6300. Simply hates them and won't boot whatever the flavour. If you have a windows cd around you could boot into its repair mode and and do an fdisk /mbr if it's totally trashed, then try the live cd again?

---

### Post by trigity on 2009-01-12
Yes the disk is very recent. I ordered it straight from Canonical it just came in the mail.

---

### Post by trigity on 2009-01-12
> **aesis05401 said:**
> Can you tell me where you are when the autorun error pops up?

There are a couple Launchpad bugs I have seen related to autorun errors, but they are distinct, and IIRC the ones I knew of have been closed.

Is your disc recent?

Yes I just got the 8.10 from Canonical in the mail very recently. I was able to reboot into the CD once a few weeks ago when i needed to use a terminal within the live cd. It's just wierd...

the error msg say's [auto running program not found] click ok!

---

### Post by ajcham on 2009-01-12
> **trigity said:**
> the error msg say's [auto running program not found] click ok!

Are you booting the disk or are you trying to run it from your desktop?  If the latter, you need to shut down your computer and boot straight from the CD.

---

### Post by trigity on 2009-01-12
> **ajcham said:**
> Are you booting the disk or are you trying to run it from your desktop?  If the latter, you need to shut down your computer and boot straight from the CD.

Yes I shutdown then powered back-up with the disk in and the same happens???

---

### Post by ajcham on 2009-01-12
> **trigity said:**
> Yes I shutdown then powered back-up with the disk in and the same happens???
Just to help us understand a bit better, at which point *exactly* do you get the error? Try and walk us through it. Do you get as far as selecting "Try Ubuntu without any change to your computer"?  Does it give the error before then, or after?  Before you get to the desktop, or after?

---

### Post by trigity on 2009-01-12
> **ajcham said:**
> Just to help us understand a bit better, at which point *exactly* do you get the error? Try and walk us through it. Do you get as far as selecting "Try Ubuntu without any change to your computer"?  Does it give the error before then, or after?  Before you get to the desktop, or after?

It doesn't even make it to selection option."Try Ubuntu without any change to your computer". It's automatically going to desktop I'll dbl clk the cd icon clk autorun prompt thats when the error pops up. I've tried several combos.

---

### Post by aesis05401 on 2009-01-12
Huh, 

I'm not sure that I quite understand as this is not anything like what happens when I put in a live cd. 

Just to be sure our fundamentals are covered, the desktop you are seeing is not your standard desktop... right?  ie: you did not remove your optical device from the boot sequence for security at some point in the recent past have you?

Anyhow, here is the reply I was typing until I saw your most recent response:
I hope someone else has a better answer for you, but these are some of the things I would do before trying a new optical drive in the machine:

1. Insert live cd into a different computer, and if it boots then verify the disc from the menu - if it checks out then the optical drive in your other box is likely the issue.

2. Attempt to use a different bootable disc in the machine that is throwing errors with the Ubuntu disc - if another disc works then contact Canonical about the media they sent you - as that may be the issue.

3. If you have a hypervisor available (I use VirtualBox) then select a working VM, change the boot sequence to include your optical drive, ensure that the live cd image will be mounted on VM load, and see what happens. 

All of these are designed to get to the same point - figuring out if the disc or your drive is suffering the meltdown.  And for the record, none of the bugs I had seen were straight error-outs like the one you are describing.

---

### Post by ajcham on 2009-01-12
> **trigity said:**
> It doesn't even make it to selection option."Try Ubuntu without any change to your computer". It's automatically going to desktop I'll dbl clk the cd icon clk autorun prompt thats when the error pops up. I've tried several combos.

Sounds like you're not in fact booting from the CD - as soon as your computer starts up enter the BIOS/Setup menu (usually F2 or Esc - it should say on screen) and check the boot order.  Make sure CD is listed before Hard Disk (example below - yours probably won't look exactly the same, but it should be similar) then save and exit. Alternatively, F12 usually brings up a boot device menu, and you can select to boot from the CD there.

[IMG]http://icrontic.com/images/mm/Articles/build_computer/bios/bios03.jpg[/IMG]

When you successfully boot the CD a message will appear at the top of the screen (something like 'ISOLINUX 3.36 Debian . . . Peter Anvin').  This will be followed by an option to select a language, and then the option to "Try Ubuntu without any change to your computer" will appear.  If this doesn't happen, (if you start seeing the Ubuntu progress bar straight away) then you are still booting from the hard-disk.

---

### Post by trigity on 2009-01-12
> **aesis05401 said:**
> Huh, 

I'm not sure that I quite understand as this is not anything like what happens when I put in a live cd. 

Just to be sure our fundamentals are covered, the desktop you are seeing is not your standard desktop... right?  ie: you did not remove your optical device from the boot sequence for security at some point in the recent past have you?

Anyhow, here is the reply I was typing until I saw your most recent response:
I hope someone else has a better answer for you, but these are some of the things I would do before trying a new optical drive in the machine:

1. Insert live cd into a different computer, and if it boots then verify the disc from the menu - if it checks out then the optical drive in your other box is likely the issue.

2. Attempt to use a different bootable disc in the machine that is throwing errors with the Ubuntu disc - if another disc works then contact Canonical about the media they sent you - as that may be the issue.

3. If you have a hypervisor available (I use VirtualBox) then select a working VM, change the boot sequence to include your optical drive, ensure that the live cd image will be mounted on VM load, and see what happens. 

All of these are designed to get to the same point - figuring out if the disc or your drive is suffering the meltdown.  And for the record, none of the bugs I had seen were straight error-outs like the one you are describing.

Alright I went to my desktop up-stairs and the CD boots fine. Gives me all the options to do whatever. So it's not the disk. Heres a quick screen shot. I apologize for my lack of knowledge I'm still GREEN... Everything works fine on my laptop, Ubuntu 8.10 has been installed and works. No  windows I got tired of everything getting viruses and crashing around me every other day... I dedicated my Acer 4315 to Ubuntu only. The Cd booted fine like 2 wks ago. But today???? I don't know

---

### Post by ajcham on 2009-01-12
Did you check the BIOS? (See my previous post. #11)

---

### Post by trigity on 2009-01-12
I might of removed [Just to be sure our fundamentals are covered, the desktop you are seeing is not your standard desktop... right? ie: you did not remove your optical device from the boot sequence for security at some point in the recent past have you?] So how can I fix my laptop to boot from the CD would I have to change that in BIOS???

---

### Post by aesis05401 on 2009-01-12
See ajcham's posting #11.
And if ajcham's boot sequence check yields nothing then grab an MS install disc or something and try that in the Acer as per #2 in my last.  If that does nothing then the Acer needs a new optical.

Gotta check out for the night.  Have fun all, and good luck.

---

### Post by trigity on 2009-01-12
Thanks for all your help. I'll work on it a bit. If I've still got issues I'll post again tomorrow. Goodnight

---

### Post by trigity on 2009-01-12
> **ajcham said:**
> Sounds like you're not in fact booting from the CD - as soon as your computer starts up enter the BIOS/Setup menu (usually F2 or Esc - it should say on screen) and check the boot order.  Make sure CD is listed before Hard Disk (example below - yours probably won't look exactly the same, but it should be similar) then save and exit. Alternatively, F12 usually brings up a boot device menu, and you can select to boot from the CD there.

[IMG]http://icrontic.com/images/mm/Articles/build_computer/bios/bios03.jpg[/IMG]

When you successfully boot the CD a message will appear at the top of the screen (something like 'ISOLINUX 3.36 Debian . . . Peter Anvin').  This will be followed by an option to select a language, and then the option to "Try Ubuntu without any change to your computer" will appear.  If this doesn't happen, (if you start seeing the Ubuntu progress bar straight away) then you are still booting from the hard-disk.

That was IT boot order was all jacked up I got now... thanks so much for your help. I should of checked that straight away. Thanks again The [NOOB] trigity:lolflag:

---

