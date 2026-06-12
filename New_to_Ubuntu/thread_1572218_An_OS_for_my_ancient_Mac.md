---
title: "An OS for my ancient Mac"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by mg1234 on 2010-09-10
I've just found my old Mac iBook. After reinstalling it completely, I find that it works fine, but its nevertheless slow, and the soft/hardware is effectively obselete. I think that linux is the answer. I want an operating system that is fast and lightweight, but still attractive. It should be updated relatively often, and have a good community base. Any ideas?

I have a Mac iBook from 2001(ish) running OSX 10.3.9 on a PowerPC 750 G3 processor, with 128MB RAM. It has 18.63GB Hard Disk.

---

### Post by moore.bryan on 2010-09-10
I've had luck with a straight Debian install and Openbox. XFCE worked well, too, but not nearly as quick as Openbox.

---

### Post by mg1234 on 2010-09-10
Thanks for the quick reply. So, what is Openbox and how do I use it?

---

### Post by NearlyALaugh on 2010-09-10
Openbox is a lightweight window manager. Others include IceWM and FluxBox. They're lightning fast but require more manual configuration. XFCE is a full-fledged desktop environment, and as such is easier—and slower. Look them up on Wikipedia.

[http://en.wikipedia.org/wiki/Openbox](http://en.wikipedia.org/wiki/Openbox)
[http://en.wikipedia.org/wiki/Fluxbox](http://en.wikipedia.org/wiki/Fluxbox)
[http://en.wikipedia.org/wiki/Icewm](http://en.wikipedia.org/wiki/Icewm)
[http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)


From a minimal Debian network install, you can install packages as desired. It's great. Be prepared to learn a lot—and get frustrated.

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)


See also ArchLinux, a lightweight DIY distribution. It's not Debian-based like Ubuntu and its derivatives so it uses its own package manager, but the wiki has all kinds of great info on configuring lightweight systems.

[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)


A lightweight Ubuntu-based distribution is CrunchBang Linux, which comes pre-configured with Openbox.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by mg1234 on 2010-09-11
Crunchbang Linux looks promising. I can't seem to find any system requirements though; does it support PowerPCs?

---

### Post by ronnielsen1 on 2010-09-11
[http://powerpup.yi.org/](http://powerpup.yi.org/)

Beta of Puppy linux PPC

[http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)

Arch Linux PPC

Both of these would be lightweight

---

### Post by coffeecat on 2010-09-11
> **mg1234 said:**
> does it support PowerPCs?

I think the previous posters (previous to post #5) might have missed this important point. My apologies to them if they did not.

Unfortunately there's not much around compiled for the PPC processor. Ubuntu withdrew official support in 2007 (iirc) although there is a community supported version of Ubuntu for the PPC. However, with only 128MB RAM, you're not going to be able to run Ubuntu/gnome. One of the lightweight desktops already suggested will be necessary but that will limit your options even more.

Have a look here:

[http://penguinppc.org/about/distributions.php](http://penguinppc.org/about/distributions.php)

It's a place to start.

**Edit:** there was a PPC section in this forum, here:

[http://ubuntuforums.org/forumdisplay.php?f=133](http://ubuntuforums.org/forumdisplay.php?f=133)

... but it was archived and made read-only in 2008. Much of the stuff there will be out-of-date but you might find some useful information.

---

### Post by NearlyALaugh on 2010-09-11
> **coffeecat said:**
> I think the previous posters (previous to post #5) might have missed this important point. My apologies to them if they did not.I sure did.

I guess CrunchBang only supports 32- and 64-bit architectures. Sorry. :-/ 

I used a minimal Debian installation for quite a while. All the graphical applications work, you just hafta choose what to install and configure the desktop a little more. But this gives you total freedom.

I've never tried Arch but it looks pretty neat too. It just puts you out of the Debian family.

---

### Post by Kixtosh on 2010-09-11
If you can get your RAM up a bit, you'll be in much better shape. Most of the LXDE desktops run lighter than XFCE in my experience, by quite a bit too, and you should even be able to boot up in no more than one minute.

I'll confess to being completely ignorant about PPC installation, however, but if it is compatible, then I have an old iMac myself from the same era that I might be able to rescue as well.

Of all the lightweight distros, Puppy is the easiest to try out in my opinion, but some find the desktop a bit, ... well, ... not very sophisticated, shall we say?! If Puppy does work with your existing 128MB of RAM (and it should - work with just 128MB, I mean - I'm not commenting on the PPC aspect) then you can decide if you want some other distro instead, and if you want to find some cheap extra RAM on eBay or something. The other thing about Puppy is it boots from a CD, and installs itself in RAM, so it won't do anything to mess up your hard drive. It's also much faster to load on old machines than any Live CD I've ever used.

My old PII/PIII 256MB RAM machines from the Win98SE era are great little kitchen browsers, but they do not support any extra RAM, or I would try to add another 128 or 256MB for good measure (and to limit the use of swap). I'm not quite sure what information the System Monitor actually shows, but when I use it to check the resources being used on my LXDE systems, they usually show anywhere from 55MB to 105MB of RAM being used ... always less than 100MB unless the Chromium browser is open.

I hope this adds to the discussion, and that it's not useless information because of the PPC thingy. ;)

---

### Post by moore.bryan on 2010-09-12
What everyone's writing is dead-on; in order of speed (purely by my experience): Openbox, LXDE, XFCE. Ease of use/learning curve?: XFCE, LXDE, Openbox. So, I would probably try-out LXDE...

---

