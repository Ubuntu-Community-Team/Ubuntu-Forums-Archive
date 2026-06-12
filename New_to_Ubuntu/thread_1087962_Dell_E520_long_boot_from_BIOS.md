---
title: "Dell E520 long boot from BIOS"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by ubername on 2009-03-05
HI

This is not Ubuntu related but this is far and away the best forum and the header
**Absolute Beginner Talk**
The perfect starting place to find out more about computers, Linux and Ubuntu.

seems to accommodate my request for info, so here goes:

I have a Dell E520 which takes +-20 seconds to go from the basic BIOS boot screen (black and white after the initial boot screen with a blue bar and the Dell logo) to my grub menu.

On my other system (Dell 4600) the grub menu appears almost instantly after the initial 'blue bar' screen.

I have a hunch this has to do with the fact that the E520 HD is controlled by RAID BIOS (although it is not RAIDed in anyway as far as I know: I have all the space available to me that the drive size suggests).

Anyone have any clues or is it just 'the way it is'?

---

### Post by kanikilu on 2009-03-05
This is a long shot, but do you by any chance have an external SATA (eSATA) drive attached to the system? I was puzzled that my POST time on my Dell XPS 420 went from a blink of an eye to ~30 seconds. After back-tracking things I had changed, I tried unplugging the eSATA drive, and everything was back to normal. It only did this while using eSATA, USB was no problem.

...I never did figure out why that happened, I just reused the external enclosure on my Mac for TimeMachine...

---

### Post by ubername on 2009-03-05
> **kanikilu said:**
> This is a long shot, but do you by any chance have an external SATA (eSATA) drive attached to the system? I was puzzled that my POST time on my Dell XPS 420 went from a blink of an eye to ~30 seconds. After back-tracking things I had changed, I tried unplugging the eSATA drive, and everything was back to normal. It only did this while using eSATA, USB was no problem.

...I never did figure out why that happened, I just reused the external enclosure on my Mac for TimeMachine...

Thanks for the reply. AFAIK I don't have a SATA or eSATA drive attached. I have a USB drive attached but the slow booting pre-dated that. I am a bit of a novice around hard disk classification. Could Dell have sent me a standard E520 with eSATA Hard drive?

---

### Post by hdz on 2009-03-05
There is a setting in most Bios/cmos setup for fastboot.  It just doesn't check every single setting that can be performed on boot (which most of the time it doesn't need to) when set ON.  try f1 f2 f10 f12 del whatever to get into your cmos setup see if that helps any.  And yes, the order of boot devices would help gain a few seconds if that, but I'm sure it's that or another setting.

---

### Post by kanikilu on 2009-03-05
eSATA would be an external drive, plugged into the back of the computer. You'd probably know if you had one.

Can you try it without any external drives (USB included) attached? I know you said it pre-dates the problem, but...worth trying. If that doesn't work, start unplugging non-essential USB devices one at a time and try again (printer, webcam, etc.).

Also, this shouldn't cause a 20 second delay, but you might try putting your hard drive at the top of the boot order list in your BIOS to see if that helps at all.

I can't really think of anything else off hand. From there I'd probably start doing very generic diagnostics: memtest, hard drive manufacturer's diagnostics, and any built-in diagnostics the computer has (on a Dell, I think press F12 at POST and see if there is a "run system diagnostics" option).

---

### Post by ubername on 2009-03-07
Thanks all

Unhooking all externals has not helped, I'm still messing with various boot options. I thin k it might just be 'the way things are' although I am still somewhat confused by the message 'This drive is controlled by the RAID BIOS' for my only hard drive.

---

### Post by ubername on 2009-03-12
I have tried using the Dell support forums for this and discovered to my surprise that there are fewer members logged on than there are moderators on this site(!) so forgive my persistence in this forum.

It crosses my mind that my Dell E520 has one of those 'multi card readers' attached (in the main computer, not via USB). Does this perhaps cause the problem? Also, I am not getting anyone confirming the problem or saying 'I have a Dell E520 and it boots sharpish from the BIOS to the MBR'. Can anyone help?

TIA

---

### Post by skymera on 2009-03-12
I have (had) the Dell E520 (It's under my bed, collecting dust)
Make sure Fast Boot is enabled in the BIOS.

Press "F2"? on boot and make sure Fast boot is on.
This should shorted the BIOS screen significantly.

---

### Post by ubername on 2009-03-13
> **skymera said:**
> I have (had) the Dell E520 (It's under my bed, collecting dust)
Make sure Fast Boot is enabled in the BIOS.

Press "F2"? on boot and make sure Fast boot is on.
This should shorted the BIOS screen significantly.

Thanks, already done that to no avail.

---

### Post by ubername on 2009-03-15
Sorry to be a nuisance, but can  I just check whether my situation is unusual or not:

Is three anyone out there  who uses a Dell E520 which boots more quickly than the +- 20 seconds I experience from the initial bios display?/

---

### Post by ubername on 2010-01-03
Found out the problem - for some reason the computer was shipped with RAID switched on (although there is only one HDD in it). Switching this off (actually to 'autodetect') causes the grub menu to come up straight away from bios load. However the windows install(s) don't like this. (*buntu and e.g. SUSE are not troubled). So I have the RAID option in BIOS set to 'autodetect' most of the time, and then if I want to boot Windows I have to switch RAID on, and wait for half a minute between BIOS boot and GRUB menu.

---

