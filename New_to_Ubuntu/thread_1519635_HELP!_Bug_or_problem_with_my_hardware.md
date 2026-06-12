---
title: "HELP! Bug or problem with my hardware??"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by bigwigbaz on 2010-06-28
I have had problems with 10.04 since installing, I have resized my 8.04 install on my Dad's machine which is mostly used for digital photos, not much else. 

Every so often and without warning the desktop will suddenly crash, it appears to show a corrupted 'ubuntu' splash logo then some text about checking battery state, it is never up for long enough to get a photo. It will then start flashing vertical black and white bars at the top of the screen while the lower half is black. This continues...

I have to do the Alt+SysRq+REISUB to reboot. Ctrl+Alt+F1-6 does nothing. It appeared initially this was only when loading certain pages in firefox, though it is still happening now I am using Chromium. It seems to be happening less though lately, though I have been using the 8.04 install. 

Nothing has been imported and it is not an upgrade, I am dual booting. I do not want to start using another system but will if this problem cannot be resolved. 

I think I need to be checking logs etc. but don't know what i'm looking at. 

Thanks in advance, Matt

---

### Post by nhasian on 2010-06-28
did you say you are dual booting between 10.04 and 8.04?  does this problem happen in both Ubuntus? or only in 10.04?

---

### Post by bigwigbaz on 2010-06-28
Thanks for the prompt response, 8.04 still works perfectly but updates will cease soon so I wanted the next LTS version. I have installed default, EXT4 filesystem and bootloader (grub 2) installed.

---

### Post by nhasian on 2010-06-28
are you on a laptop?  how old is the battery? have you tried disabling the power management features?

you could also try the latest stable linux kernel 2.6.34

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

you will need to install 3 packages.

> For 32 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)

> for 64 bit:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb)

please install in order listed.  Then run from a from a terminal afterwards:

```
sudo update-grub
```

reboot.  to confirm you are running the new kernel type in a terminal:

```
uname -a
```

---

### Post by bigwigbaz on 2010-06-29
No it's a desktop machine, set power management off, so no spinning down disks, I even disabled the screen saver as I initially thought it was this causing the problem. 

I have downloaded the three packages, but what do I need to do with them? I guess open nautius in root mode and just double click? This sounds a surprisingly easy way to upgrade the kernel!

I have run the uname -a command, it returns 2.6.32.xx (on another machine now)

I will give it a try when I get to the machine. 

many thanks, Matt

---

### Post by nhasian on 2010-06-29
not necessary to open nautilus in root mode.  simply right click on the deb file to install it.  it will prompt you for the password.

---

### Post by bigwigbaz on 2010-06-29
Many thanks, Nhasian, the boot splash image showed much smaller this time, other than that all seems ok. 


matt@matt-desktop:~$ uname -a
Linux matt-desktop 2.6.34-020634-generic #020634 SMP Mon May 17 20:34:55 UTC 2010 i686 GNU/Linux


Looks all good. I will keep an eye on it over the coming weeks and report back if there's any further issues. 

Once again, thanks. 
:guitar:



Now how do I mark this thread as solved??!!! LOL

---

### Post by bigwigbaz on 2010-06-29
No, gone again, just this time the text was smaller and no vertical bars on the screen. Again too quick to catch with my camera. 

At a bit of a loss here, might look into another distro.

---

### Post by bigwigbaz on 2010-07-02
[IMG]http://i850.photobucket.com/albums/ab68/bigwigbaz/DSCF2313.jpg[/IMG]


Gone again, this time with a fresh install of Lubuntu!

Any ideas, message says about unknown user id, GLib-warning...

This is very similar to the messages I was getting with the ubuntu 10.04 install. My 8.04 is still working fine.

---

### Post by sydbat on 2010-07-02
What are the specs of the box? Might be a newly unsupported piece of hardware?

Also, and this might sound stupid but, are there any other OS's on this box? If so, how did you install both Hardy and Lucid? In their own partitions? Via wubi?

More info from you will help us.

---

### Post by bigwigbaz on 2010-07-02
> **sydbat said:**
> What are the specs of the box? Might be a newly unsupported piece of hardware?

Also, and this might sound stupid but, are there any other OS's on this box? If so, how did you install both Hardy and Lucid? In their own partitions? Via wubi?

More info from you will help us.

Hi SYDBAT, 

The box is quite an old Dell dimension 2600 I think, I have only an 80GB IDE drive and the machine is used mostly for digital pics and net browsing. There are 2 optical drives, an old Sony CD-RW and a newish LG DVD-RW. There is nothing else attached, no peripherals. I only want a basic machine that my Dad can use for pics, net and basic office apps. I felt I should upgrade when 10.04 became available as the updates for 8.04 will end soon. 

The OSes are on their own partitions, just 8.04 (xubuntu) Roughly 50GB and 10.04 lubuntu roughly 26GB plus a swap partition of about 1.2GB. I installed 10.04 gnome from usb using the USB creator tool in 9.10 (wubi install on another machine), then installed Lubuntu by the same method. I had an error when installing the LXDE version, something about a drive being mounted, unmounted and restarted the install process (from live desktop) and all ok. 

The strange thing is that the 8.04 is fine, but both gnome and LXDE versions of 10.04 have the same problem.

---

### Post by sydbat on 2010-07-02
Unless your dad needs cutting edge applications, I suggest that, if 8.04 is running fine, then stick with it. There will be updates for another few months (maybe a year).

---

### Post by bigwigbaz on 2010-07-02
Yeah I think that's the best option, then possibly install debian when updates stop...

many thanks, Matt

---

