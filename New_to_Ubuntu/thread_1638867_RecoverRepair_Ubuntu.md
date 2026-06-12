---
title: "Recover/Repair Ubuntu"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by anweshdbest on 2010-12-06
I have Ubuntu 10.10 and by mistake i removed some packages using the Synaptic Package Manager and now all i get is the low graphics Ubuntu (CUI) in nature!

I tried configuring which didn't work, i even tried recovery mode, and repairing broken packages, which too was to no avail.

Please help me recover or repair my installation..

OR if this is not possible

please tell me how do i take a backup of a certain folder which is on my Hard Drive!

Ubuntu was the only OS installed..

---

### Post by diablo75 on 2010-12-06
Here's a couple options

1.  Try your best to reverse what you did by reinstalling the packages you removed, and everything else involved with restoring settings associated with whatever they were.

2.  Use a Live CD to boot up, giving you access to your hard drive allowing you to backup anything you need to from your home folder or elsewhere, and then just reinstall.

I know some guru linux users out there would opt for the first because they really, really, really want to know what went wrong... and in a slight way, punish themselves for screwing up.  I, on the other hand, opt for the solution that is bullet proof, and perhaps time saving, and so if I were you (or if you were me???) I would opt for the second option.  Start from square one with a fresh install and rebuild that way.

---

### Post by anweshdbest on 2010-12-06
What is a LIVE CD?

The one that i have doesn't allow any recovery options.

Just allows to try ubuntu and install it!

---

### Post by diablo75 on 2010-12-06
> **anweshdbest said:**
> What is a LIVE CD?

The one that i have doesn't allow any recovery options.

Just allows to try ubuntu and install it!

Live CD is just a CD that you can boot from.  Computers are capable of booting from any number of devices/media, and you can tell a computer to check different sources for a boot image when you turn the computer on.  In the old days, the primary boot device was the floppy drive, followed by the CD-ROM drive, and then the hard drive.  So if nothing was present in the first drives, the HD would boot because it's the only thing left with something on it that can be booted.

These days many PCs don't check the CD-ROM or USB ports before the hard drive, unless you specifically tell it to do so.  Some computers have "Boot Menus" that you'll see offered right after you turn your computer on ("Press F12 for boot menu").  You can also go into your BIOS to manually adjust the boot order/priority.  You should make the CD-ROM your first boot device.

It's quite likely you have a Live CD in your hands and that you can boot from it.  Installing is simply a matter of booting from the CD, letting it load up, and telling it you want to install.  It's really simple.

---

### Post by owiknowi on 2010-12-06
> **anweshdbest said:**
> What is a LIVE CD?

The one that i have doesn't allow any recovery options.

Just allows to try Ubuntu and install it!

You can download a live CD from Ubuntu's website.
Burn it to a CD and boot your computer from it.
Thus you can save your files from the original installation's /home/yourusername/ directory to an external drive (USB, SD, etc.)

I even believe the original Ubuntu installation CD offers an option to repair a broken system.

If you however choose to do a fresh installation, choose for example the following partitioning (GParted or PMagic or Ubuntu also can do this):
1. partition for /root (= file system).
2. linux swap (4GB or 4096MB) should be enough.
3. partition for /home

This way you can always repair or re-install a damaged OS without loosing your personal files from the /home partition.

---

### Post by anweshdbest on 2010-12-06
But i find no option to recover or repair from the Ubuntu CD.

And when i use 'Try Ubuntu' to try and recover my data, it makes all my folders and data inaccessible rendering them impossible for me to copy!

---

### Post by nothingspecial on 2010-12-06
From the terminal in the live cd type
```

gksudo nautilus
```

Now your folders wont be locked.

---

### Post by HermanAB on 2010-12-06
Howdy,

It is very easy to repair Linux - just re-install - it only takes about 30 minutes.  

However, that works best if you have a separate /home partition - when you re-install, don't reformat it and all your data will be preserved.  If you don't have a separate /home partition, copy the data to a memory stick first, before re-installing.

---

### Post by anweshdbest on 2010-12-06
Tried gksudo nautilus, but it returned an error saying that it needs system administrator privileges or something!

---

### Post by owiknowi on 2010-12-06
Help on using a terminal as root with a live CD:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

A more extended help on data recovery with a live CD:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As a last resort you can use data recovery and rescue your files from -partition name-/user/yourusername to external media or an other partition:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

