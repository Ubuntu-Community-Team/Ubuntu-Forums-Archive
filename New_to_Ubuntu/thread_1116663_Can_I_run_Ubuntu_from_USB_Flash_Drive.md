---
title: "Can I run Ubuntu from USB Flash Drive?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by jugolam on 2009-04-05
My motherboard only supports these as boot device. Can I run Ubuntu from USB Flash Drive?

Floppy
LS120
Hard Disk
CDROM
ZAP100
USB-FDD
USB-ZIP
USB-CDROM
Legacy LAN

Thanks!

---

### Post by zigga15 on 2009-04-05
Do you mean install it from a USB drive??

I would recommend running it from a hard drive.

If you run it from a usb drive there will be a lot of read/writes and ur usb drive will break in about 1 week. Also it would take forever to do anything. Very bad idea.

Ubuntu 8 is a live CD, run it from there if you need something "temporary :S ?"

~ Dan

---

### Post by dandnsmith on 2009-04-05
Look at pendrivelinux.com for methods of installing to a usb stick, in particular a persistent install.

What this will get you is a usb-stick with a version of the live CD installed in such a fashion that you can customise the configuration and have the changes saved.

I'd recommend having somewhere on a hard disk to save stuff which you want to work on, to reduce the writes to the usb-stick.

Further, you can find (on pendrivelinux) a method of testing your system to see if it can boot from a usb-stick. I suspect from what you list that you'll find it cannot. If so, the nearest I've seen is a [posting](http://ubuntuforums.org/showthread.php?t=1103247) which talks about a method of configuring a stick as if it were a superfloppy (which I think is your LS120).

---

### Post by mlentink on 2009-04-05
I run Ubuntu NBR from a flash drive in my netbook. Do not install swap, as this might shorten the live-span of your flashdrive. Other than that, you should be fine for the next couple of years.

---

### Post by Paqman on 2009-04-05
You certainly can, but i'd recommend using an 8GB stick, the 4GB ones are just a wee bit too small. As mentioned, I wouldn't use it as your main system, as the stick will wear out.

You can reduce disk writes by taking some of the same steps people use to [reduce wear on SSDs]("http://www.brighthub.com/computing/linux/articles/9170.aspx"). I personally think they're being needlessly paranoid on SSDs, but on a memory stick you absolutely want to take these measures, since memory sticks don't have any kind of built-in wear leveling.

---

### Post by jmszr on 2009-04-05
jugolam,
        This is an alternative that might work for your needs - it just came out and here is a discussion from the Community Cafe: [http://ubuntuforums.org/showthread.php?t=1116392](http://ubuntuforums.org/showthread.php?t=1116392) and the more comprehensive write up from Lifehacker: [http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows) .

As I said, it is new, and I haven't tried it out yet, but it looks like a possibility.

P.S.: I noticed in the documentation that the Administrative Password = 123456

---

### Post by albinootje on 2009-04-05
> **jugolam said:**
> 
USB-FDD
USB-ZIP
USB-CDROM

I've tried on a machine with similar BIOS options and couldn't get it to boot from an usb stick. 
I'd try usb-zip first or the "instant" boot-menu (usually the F12 key). Good luck.

---

### Post by Peter09 on 2009-04-05
I had an old DELL - it appeared that it would not let me boot from the USB, however on investigation I found that if a bootable USB stick was in the connector the option would appear.

---

### Post by jugolam on 2009-04-05
Thanks for all the replies.

I've done all I could today.

1. I created a USB Boot CD and it is working.

2. I installed Ubuntu on my USB flash drive. I followed all the instructions but do not know is it working or not.

The result:

After booting using the USB Boot CD, and I choose the menu available, the USB flash drive's LED blinks -- I'm positive that it is working.

However, after the "Starting up ..." and "Loading, please wait ..." messages, not Ubuntu, but BusyBox is loading.

I cannot continue anymore.

Need to stop here for today.

Sigh!

---

### Post by wolfen69 on 2009-04-05
> **Paqman said:**
> I wouldn't use it as your main system, as the stick will wear out.


by the time it wears out, 16gb sticks will be $5. ;)   if you go to the manufacturers website and look at the # of write cycles it can handle, it would take 16 hours a day of constant writing for 2 years, to wear out. people get too caught up in this "wearing out" thing.

---

### Post by albinootje on 2009-04-05
> **jugolam said:**
> 
However, after the "Starting up ..." and "Loading, please wait ..." messages, not Ubuntu, but BusyBox is loading.

Please try again with adding extra boot parameters, see instructions here :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Try adding "noapic nolapic", and then boot.

---

### Post by whoop on 2009-04-05
I use the "USB startup disk creator" tool in System-->Administration. I used it for a xubuntu and an ubuntu live-usb and it works great.

---

### Post by jugolam on 2009-04-06
Thanks everyone. Now, I'm able to use Ubuntu 9.04 from my USb flash drive.

One more thing, is this version the same version like Live CD or is it like the one that is installed in hard drive?

---

