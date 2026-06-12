---
title: "Odd Startup Behaviour"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by yknivag on 2009-02-02
I have just set my Dad up with Ubuntu after a long time struggling with Vista and he seems hooked already!

We're having a strange problem though with his laptop at startup...

After grub and before the GDM login screen (whilst the Ubuntu splash screen and progress bar are on the screen) the load freezes.  Completely.  Pressing and holding a key moves the small orange bar along (it stops if again if the key is released) and once the bar has moved fully right, fully left and started again then all proceeds as normal.

I've tried leaving it at that stage for up to an hour and it won't move on it's own, but press and hold a key for a few seconds and it boots without any problem at all (save the wifi).

Not a show stopping problem, but a rather odd one! :) I'd be most interested if someone with rather more knowledge could shed some light on what may be happening.

I've attached dmesg from the latest boot but I can't see anything obviously out of the ordinary.

---

### Post by tuxxy on 2009-02-02
I cant see your dmesg

---

### Post by Crafty Kisses on 2009-02-02
Can you boot into recovery mode?

---

### Post by yknivag on 2009-02-02
Hi tuxxy, sorry about that it didn't attach first time. It's there now.  Also forgot to mention, this is a clean install of Intrepid (had the same issue with the liveCD though too).

---

### Post by yknivag on 2009-02-02
> **Codename said:**
> Can you boot into recovery mode?

I haven't tried, as normal mode boots fine (typing in it now) once the key is held at the splash screen.

---

### Post by yknivag on 2009-02-03
> **Codename said:**
> Can you boot into recovery mode?

Tried this morning, and oddly enough I have the same issue.  Took a copy of dmesg as soon as the desktop came up, and the stop point can be clearly seen (I've marked it in the file).

As I was booting I had to hold down a key until "Reading files for boot..." appeared (there are several long pauses visible in the dmesg which is me letting go of the key to see if it would carry on.

The USB printer being detected makes no difference to this behaviour (the machine does this irrespective of whether the device is plugged in and did so before it was installed to CUPS too).

Any thoughts from the recovery mode dmesg would be most welcomed. It isn't really a show stopper, but this is my Dad's machine and he's not the most technically minded...

---

### Post by avtolle on 2009-02-03
Try this: when the bar hangs, have your dad press the power button once (no, don't turn it off). If he has an HP laptop or a Compaq made by HP as do I, this will allow the boot to continue without any further intervention. This problem is, for me, on 8.10; LinuxMint6; and openSUSE 11.1. HTH, and I suspect is related to the kernel used for each and something in the hardware for HP/Compaq.

---

### Post by Sorivenul on 2009-02-03
From looking over the dmesg (from the recovery mode), I find this:
> [    2.573664] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
This is also present in your first dmesg. 

Try this fix:
1. ```
sudo nano /etc/initramfs-tools/initramfs.conf
```
change MODULES=list
2. ```
sudo lsmod | sed 's/\([[:graph:]]*\).*/\1/' >> 
/etc/initramfs-tools/modules
```
3. ```
sudo nano /etc/initramfs-tools/modules
```
remove "Module", move ehci_hcd to the first place
4. ```
sudo update-initramfs -u
```

This should hopefully correct the issue, but if not, at least your modules will be loaded in the "correct" order. You can also make a backup of /etc/intramfs-tools/initramfs.conf before doing this by:
```
sudo cp /etc/initramfs-tools/initramfs.conf /etc/initramfs-tools/initramfs.conf.bak
```

You can read more about the bug [here]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710").

---

### Post by yknivag on 2009-02-03
Hi Sorivenul,

Thanks for you answer.  I had a problem running no2:
```

user@HOST:~$ sudo lsmod | sed 's/\([[:graph:]]*\).*/\1/' >> /etc/initramfs-tools/modules
bash: /etc/initramfs-tools/modules: Permission denied

```
So I ran:
```

user@HOST:~$ sudo lsmod | sed 's/\([[:graph:]]*\).*/\1/' >> /home/user/modules

```
The opened both of them with:
```

gksudo gedit

```
and copied the module list from one to the other, removing the word "Module" and moving "ehci_hcd" to the top.

My only question about this is should any new modules be added, will they be picked up automatically? or will I need now to add them to the list manually?

---

### Post by Sorivenul on 2009-02-03
> **yknivag said:**
> My only question about this is should any new modules be added, will they be picked up automatically? or will I need now to add them to the list manually?
As far as I know, they should be added automatically, but in general you'll only need to make sure the proper modules are added if you add new hardware to the machine. Like I said, do a backup to restore your old settings if needed. If you run into problems, post back here. 

Also, please let us know if this works for your setup.

---

### Post by yknivag on 2009-02-03
Thanks for that - I don't think we'll be adding any new hardware any time soon, but I guess we'll see what happens ;)

The machine still boots ok, but still hangs until a key is held.  Seems to be at a different place though (new dmesg attached)...

This is really strange!

---

### Post by Sorivenul on 2009-02-03
> **yknivag said:**
> Thanks for that - I don't think we'll be adding any new hardware any time soon, but I guess we'll see what happens ;)

The machine still boots ok, but still hangs until a key is held.  Seems to be at a different place though (new dmesg attached)...

This is really strange!
I'll take a look at the new dmesg. Thanks for your patience! Out of curiosity, and for possible further help, what kind of laptop is this?

---

### Post by jimv on 2009-02-03
Oh man, that's a terrible spot for a pause...there's no obvious problems even near there.

Here's something you can try to diagnose this while it's booting up.  When you boot up the machine, hit E on the Grub screen and remove the word QUIET from the kernel line.  The hit B to boot up.  This will show you what it's doing while it's doing it.

---

### Post by yknivag on 2009-02-04
> **jimv said:**
> Oh man, that's a terrible spot for a pause...there's no obvious problems even near there.

Tell me about it - I've been at it a week trying to identify what's happening.  It does it with the live CDs too, for both Hardy and Intrepid.

> **jimv said:**
> Here's something you can try to diagnose this while it's booting up.  When you boot up the machine, hit E on the Grub screen and remove the word QUIET from the kernel line.  The hit B to boot up.  This will show you what it's doing while it's doing it.

Excuse my ignorance (grub is not my strong point) but is this different to using the recovery mode to force a text based boot instead of the splash screen?

---

### Post by yknivag on 2009-02-04
> **Sorivenul said:**
> I'll take a look at the new dmesg. Thanks for your patience!

Not at all, thank **you** for your help! I have all year, it's my Dad's laptop and he's quite happy as it is. I'm a perfectionist though, and it's bugging me. :)

> **Sorivenul said:**
> Out of curiosity, and for possible further help, what kind of laptop is this?

It's an HP G6000. The only oddities hardware wise are that it has a built-in webcam (which works out of the box) which appears in lsusb as a USB device, and a built-in Atheros AR5007 wifi card that ath_hal mistakenly identifies as an AR242x and won't use.

I'm wondering (even though these are logged much after the pause) if either of these are causing the issue, especially the wireless card.

---

### Post by moveright on 2009-02-05
I have the same exact problem.  I have a compaq presario notebook model v6719nr.  it's AMD64 as well.  I did a livecd install from ubuntu 8.10 and then I did a full hard drive wipe clean install from 8.10x64 using alternate cd.  thought for sure that would correct my issue but no, it does not.  I agree that this is not a show stopper but I am just that anal that something like this really gets under my skin.  I sure hope one of the talented people from this forum can shed light on this.  interesting to hear the other distros which are also plagued by this.

---

