---
title: "Busybox comes up when trying to boot into all the kernels!"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by parham-d on 2010-09-08
Hi,

I have kernels 2.6.3-24, 2.6.3-22, and 2.6.3-21. However, when I try to boot into any of those, Busybox comes up, all the time with different errors. I have captured a few of them here:

"Gave up waiting for root device."
"No init found. You should have init = bootargs."
"Module not found."

And all the time, when trying to boot into 2.6.3-24, I don't even get any of these, I just get,

"Alert! /dev/disk/by-id/[the UUID here] does not exist."

Any ideas how I can fix this? I read a solution that was talking about booting to an earlier kernel, but that didn't work. Also, for some reason, when I put in a live CD/DVD, the Grub menu comes up, so I can not use the live CD to recompile initd.immg.

I'd appreciate it if one of the problems above (not being able to boot into any of the kernels, and not being able to boot any CD/DVDs) were solved.

Thanks a lot!

---

### Post by coffeecat on 2010-09-08
> **parham-d said:**
> Hi,

Hi. :)

> **parham-d said:**
> I have kernels 2.6.3-24, 2.6.3-22, and 2.6.3-21.

I think you mean 2.6.32-24, etc, which would mean you are using Lucid/10.04. Is that correct?

> **parham-d said:**
> However, when I try to boot into any of those, Busybox comes up, all the time with different errors.

Something serious has happened with your system. This is not due to a bug in an update. What were you doing just before your system became unbootable? Did you have an unclean shutdown - perhaps a power outage?

> **parham-d said:**
> "Alert! /dev/disk/by-id/[the UUID here] does not exist."

This is an important clue. All partitions are identified by their UUID - a long string of alphanumerics. The system is trying to find a particular partition, but cannot because it cannot find the UUID. This sounds very bad.

> **parham-d said:**
> Also, for some reason, when I put in a live CD/DVD, the Grub menu comes up, so I can not use the live CD to recompile initd.immg.

I'm not quite sure what you mean here. Do you mean that when you boot from the live CD, it shows its own menu, or your grub menu? If the latter then you are not booting from the live CD. Check you BIOS settings. Also - recompiling initrd.img may or may not help, but I doubt it will. You can do it from the live CD but lets see what's wrong first.

I'm going to ask you to boot into the live CD session and you will need to be able to connect to the internet from the liveCD. This is because I'm going to ask you to post some terminal output and you'll need to copy and paste from the terminal. Can you do this?

OK. Boot up the live CD. (Check those BIOS settings.) First thing, go to the Places menu and see if you can find your Ubuntu root partition there. Click on it and a file browser will open. Press ctrl-L and the breadcrumb path trail will change to a text path address bar. It will show /media/*longstring*. Make a note of that. Even better, highlight it and press ctrl-C to copy it into memory. You'll need it later.

Now open a terminal (Applications > Accessories). In the terminal, type:

```
cat /media/longstring/boot/grub/grub.cfg > ./Desktop/grub.cfg
```Obviously, substitute the long string for 'longstring'. A file grub.cfg will open on your desktop which you will be able to open by double-clicking on it. Post the contents. Now...

```
cat /media/longstring/etc/fstab > ./Desktop/fstab
```A file called fstab will appear on the desktop. Post the contents. Now...

```
sudo blkid
```Some output will appear in the terminal. Post that by copying and pasting.

With all that we might get some more clues as to what has gone wrong.

By the way, when you post those three outputs, please enclose them in code tags otherwise your post will be unreadable. The easy way to do this is to highlight what needs to be enclosed, and click the # icon just above the message field. Please do this separately for each of the three - we don't want them muddled together.

**Edit:** Hmmm. I've just found your previous thread about the same  problem. You should have continued there rather than start a new thread.  Anyway, no one can help you unless you sort out booting from CD.  Someone mentioned this on that other thread, but you did not respond.  Again - check your BIOS settings. If your live CD still does not boot  then burn another one.

---

### Post by parham-d on 2010-09-08
Hi,

The problem with my previous thread was that my messages were leaving the impression that I was not being dropped into Busybox, and rather it's X Server that is failing.

Regarding the booting, yes, Grub comes up, but the DVD is being checked for being bootable, because the DVD starts to spin. After that, I am being asked for a password (I don't know what password it is) but when I enter the password I enter in every website and account, it passes, and the Grub menu comes up.

My BIOS is protected by a password. When I call the laptop support where I bought this laptop from five years ago, they say they do not keep the passwords for laptops older than three years. However, before installing Grub, the DVD booted fine. Since this is a laptop, I don't think the DVD is not being checked, because 1, it spins, and 2, there is nothing else to check, just the harddrive.

Yes, this happened after my laptop crashed and I hard-rebooted (I.E. held down the power button, then turned it back on).

And yes, I am using Lucid 10.04.

---

### Post by coffeecat on 2010-09-08
> **parham-d said:**
> Regarding the booting, yes, Grub comes up, but the DVD is being checked for being bootable, because the DVD starts to spin. After that, I am being asked for a password (I don't know what password it is) but when I enter the password I enter in every website and account, it passes, and the Grub menu comes up.

I don't really follow what's happening here - particularly what yo mean by passwords. If by 'grub menu', you mean the menu on your hard drive then clearly the BIOS is not booting from the CD. 

> **parham-d said:**
> My BIOS is protected by a password. When I call the laptop support where I bought this laptop from five years ago, they say they do not keep the passwords for laptops older than three years.

Do you mean that the laptop was shipped with a BIOS password set? I would have thought that's most unusual.

> **parham-d said:**
>  However, before installing Grub, the DVD booted fine.

If you're implying that installing a grub menu stopped the machine booting from the DVD drive then, no, that's not possible. Device boot order is set in the BIOS. If you can't get into the BIOS then I don't know what you can do. You have to be able to boot from a CD or DVD to have any hope of repairing your system.

The only other thing I can suggest is that perhaps the DVD you are using has been damaged or cannot be read for some reason. If the laptop is spinning the DVD first but then going on to the HD grub menu then, perhaps yes it is checking to see if it's bootable and finding it is not. In which case you need to burn another CD/DVD and try that.

---

### Post by parham-d on 2010-09-08
> **coffeecat said:**
> I don't really follow what's happening here - particularly what yo mean by passwords. If by 'grub menu', you mean the menu on your hard drive then clearly the BIOS is not booting from the CD. 

Yes. That is exactly what I mean. It is not booting from the CD/DVD, and is instead asking me for a password.
> 
Do you mean that the laptop was shipped with a BIOS password set? I would have thought that's most unusual.


Yes, it was. I found the password though. But get ready to read something very strange. None of the keys that I have found through the Internet now enter the bios setup. Escape doesn't work, f1 doesn't work, neither f2, nor f3, nor f4-f12. Even the delete key which up to this point would let me enter bios setup doesn't work. Instead, this "enter password" prompt comes up, and as soon as I enter the password and press enter, the Grub menu on my harddrive comes up. The CD doesn't boot, the DVD doesn't boot, and believe me, I have tried. I have tried a Debian live CD, Ubuntu, Windows XP, nothing. They are all the same; they don't boot. Oh, and another strange thing. My USB harddrive was plugged in during the installation, and I told Ubuntu to install alongside Windows. Now, when I turn on the laptop without the USB harddrive attached, the Grub menu doesn't come up at all. I get a message that [something] was not found.

> 
If you're implying that installing a grub menu stopped the machine booting from the DVD drive then, no, that's not possible. Device boot order is set in the BIOS. If you can't get into the BIOS then I don't know what you can do. You have to be able to boot from a CD or DVD to have any hope of repairing your system.


Trust me. There were no problems before this point. I could boot the same CD/DVDs that now won't boot at all. I could enter the BIOS setup. I can't do either now, and instead have to enter my password, after which the Grub menu comes up (that is, if my USB harddrive is attached. Otherwise I'll receive an error).

---

### Post by coffeecat on 2010-09-08
OK, I'm getting a better idea of what's going on now. It does sound as though something has gone very awry with the BIOS. If this was a desktop I would suggest resetting the BIOS to its default state with the motherboard jumper but I guess that won't be an option here.

I'm sorry. I'm out of ideas except for one thing...

If you can take the hard drive out and if you can get hold of a USB enclosure for it (you'd have to check whether the HD is a newer SATA or an older parallel in order to get the correct enclosure), you would be able to access the contents of the drive from another machine. You'd even be able to do a fresh install from another machine if you decided the old system was beyond repair.

Some thoughts about that though. If you are not able to borrow a 2.5 inch enclosure that would be a significant expense which you might not want. And also - as I said in my first post - the error messages you were getting suggest a serious corruption of your installed system. Add that to a BIOS which has started behaving in a strange way and I would be wondering if something happened which damaged both the BIOS and the installed system. A surge in the mains? A discharge of static? In short - is the laptop damaged beyond economic recovery? Sorry to be gloomy, but I leave that thought with you.

---

### Post by parham-d on 2010-09-08
Hi,

Maybe I can give the laptop back to the support so they could reset the bios? I'll call them tomorrow and see.

---

### Post by coffeecat on 2010-09-08
Good luck with that. I hope they can.

---

