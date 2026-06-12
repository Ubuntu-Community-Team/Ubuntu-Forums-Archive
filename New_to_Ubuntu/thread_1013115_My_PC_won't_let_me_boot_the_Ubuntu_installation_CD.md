---
title: "My PC won't let me boot the Ubuntu installation CD"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by applesanity on 2008-12-16
New here.  I want to try out Linux.  After much research, most roads led me to Ubuntu.

I downloaded Ubuntu and put it on a CD.  Upon running the CD, it asked me to reboot.  So when I rebooted, it just went straight to the Windows XP login.  I ran the CD again, and I found the option to configure windows to boot from the CD.  I tried that and when I rebooted, I came to a screen that asked to choose either XP home edition or Ubuntu.  When I chose ubuntu, the screen went dark for awhile, then I was led back there again. I repeated, same effect.  When I click on the choice to load XP, everything goes as normally in an XP startup.

When I start up my 5 year old computer, the first thing I see is the VAIO logo (it's a sony), then the "Intel Pentium 4" logo, then the Windows XP load.

I never get the screen that displays "press F12" for boot options.  What do I need to do to make my computer load Ubuntu?

Thanks!

---

### Post by Cornbreadly on 2008-12-16
This happened to me once.

Look up your Vaio model on the internet and find its specs.  Take note of the motherboard.  Then you can google the mobo model with the words "bios" and get info about how to edit the settings that way.  Vaio were popular and someone was bound to have runinto this problem before.

Or... just start hitting "f#" keys are reboot.  You'll probably get lucky.

---

### Post by mapes12 on 2008-12-16
Some how you need to be able to get into your BIOS to change boot devices to your CD-ROM. If you can get a copy of your machines manual from somewhere then that should help you out.

---

### Post by fiddler616 on 2008-12-16
First of all:
Did you *unpack* the .iso onto the CD? Or just copy it? .iso is the CD version of a .zip--the raw file won't do squat for booting.

On my Vaio, I press F2 immediately upon seeing the Vaio logo, and then use the arrow keys to navigate to the boot section. I seem to recall that pressing <Enter> from the splash screen will bring up a boot-only, popup mini-BIOS though.

---

### Post by Hospadar on 2008-12-16
(If the F2 suggestion above doesn't work)
Though it is crude and barbarric, I would suggest mashing all your F# keys, backspace, delete, maybe some other keys if those don't work.  Keep doing this until you get into a bios menu, it'll probably be blue, with all sorts of options, cruise around it until you can find the boot order, set the CD drive first and see what you come up with.

Also as above, make sure you burned the cd correctly.  When you browse it from windows, do you see a bunch of files, or do you just see ubuntu_<somethingorother>_.iso

---

### Post by fiddler616 on 2008-12-17
Now that I think about it, the quick boot menu is <Esc>, not <Enter>...

---

### Post by redandgreen on 2008-12-17
Pressing 'pause' as soon as your computer starts will pause the boot. Hit all the F keys, and delete for good measure, then press enter (or it is pause again?), and you should head straight into the bios.

---

### Post by fiddler616 on 2008-12-17
> **redandgreen said:**
> Pressing 'pause' as soon as your computer starts will pause the boot. Hit all the F keys, and delete for good measure, then press enter (or it is pause again?), and you should head straight into the bios.
*I *thank you for the tip--I didn't know that.
...hmm...where'd the OP go?

---

