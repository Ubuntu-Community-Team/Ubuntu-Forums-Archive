---
title: "Secondhand Ubuntu 10.10 - No CDROM Boot, no boot menu, no GRUB."
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Baldran on 2011-08-17
I recently received a Mac iBook G3 running Ubuntu 10.10. I do not know the password for the account already on it, so I'd like to either reset it or reinstall the OS entirely. Here's where I run into problems, though:

-After the Mac startup chime, the first prompt I get is "First Stage Ubuntu Bootstrap", which lets me press 'l' to boot the GNU/Linux on the computer, or 'c' to boot from a CD-ROM. However, pressing 'c' gives me a 'Booting CDROM' message, and then does nothing. I have left it in this state for several hours, and no progress is apparent. This is with a Ubuntu burn disk in the CDROM drive

-Additionally, attempting to boot the CD from the OpenFirmware command menu automatically adds 'load-size=0 adler32=1' to the command line, and returns the message 'LOAD-SIZE is too small'

-Past this step, the computer will automatically boot the Linux kernel on the machine. Holding 'Shift' will not bring up the Boot Menu at any point in the startup process, and there is no GRUB command line anywhere that I can use to bring it up otherwise.

So, I guess what I'm asking for is an alternate way to boot from a CDROM, or to access the boot menu, or to get a GRUB command line, or just to get around the login screen somewhere else. It'd be a shame to have to toss this perfectly good computer for a problem a silly as this.

---

### Post by elgordodude on 2011-08-17
I don't have much experience with macs, but I remember they don't have a traditional bios where you can go at atartup and change the boot selection process. I think if you hold c at startup it will force it to boot from the cdrom instead of the hard drive.

Hopefully allowing you to install a fresh os

---

### Post by Baldran on 2011-08-17
At exactly which point in the startup process should I begin to hold 'c'? It doesn't give me anything if I hold it at the same time as I push the Power button.

---

### Post by elgordodude on 2011-08-17
As I said my mac experience is limited. I only had a mac mini for about a year and I never really liked it, so it was always more of an educational toy than an actual computer.

You should hit it just after the power button, but that shouldn't matter too much. Is there an "option" button or a "apple" button, the g3 is getting a little old isn't it? 

Duh, just reread this:


> pressing 'c' gives me a 'Booting CDROM' message, and then does nothing.

Is there a way to try another cd? I'm thinking your cd may be corrupted.

---

### Post by Baldran on 2011-08-17
I also tried an OS 9 CD, with the same result.

Any advice on how to boot from a USB, given the aforementioned limitations?

In any case, is there any other way to go into repair mode and reset the password besides the boot menu, without actually having to use a password?

---

### Post by elgordodude on 2011-08-17
Well, I was told that macs can only boot from the disc that was sold with them, no idea if this is true or not, it sounds weird, but also like the sort of thing apple would do, so if it's a borrowed disc it won't, shouldn't, (should this thread be in the mac forum?) work. maybe?

If it is the original disc, than it is very rare to get two corrupted discs, and you likely have a hardware issue, most likely the cd-rom. 

As far as a usb boot goes, I would try putting a liveusb in it, turning it on, and see if it comes up with something like 'press u to boot from usb' one can hope, but it's outside my personal experience.

Someone here might be able to hack it but to my knowledge you need sudo to change the password.

---

### Post by Percivale on 2011-08-18
I am having a somewhat similar issue, except pressing buttons accomplishes nothing at all.

I'm using 11.04 on a Macbook 6,1. When I turn on the computer, I get the chime and the normal mac background, then the screen goes dark, then I see a single blinking cursor in the top left corner, followed by a garbled, distorted mess of colors, then another dark screen, and finally Ubuntu loads normally.

There is no text or graphics of any kind during the startup process.

I can hear the boot CD in the drive starting up, but nothing happens.

Holding down or tapping c does nothing; I have not tried "u" for my usb startup disk yet, I guess that's the next step.

But there is no GRUB, and I can hold down or tap shift till I get blisters on my fingers and nothing comes up.

Is there any way around this, so I can reset the password?

---

