---
title: "Which flavor  of ubuntu is recomended for an older laptop?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by lcjohn on 2009-04-22
Hello.
I have a Compaq Presario 1700 laptop with thw following specifications:

P3 700 Mhz
128 MB ram

and I'm wondering if it will run well the newest version of ubuntu?
If it will not run well, then is there another version of ubuntu that my laptop can handle?

Many thanx
LC John

---

### Post by listerdl on 2009-04-22
I have a laptop with the same-ish specs as that and i am running hardy heron works very well - ubuntu - 8.10 (I think).

Just try and see how it goes...i dont think you can do too much damage just by trying out, (i might be wrong though!)

---

### Post by porchrat on 2009-04-22
> **listerdl said:**
> I have a laptop with the same-ish specs as that and i am running hardy heron works very well - ubuntu - 8.10 (I think).

Just try and see how it goes...i dont think you can do too much damage just by trying out, (i might be wrong though!)

8.10 is intrepid ibex not hardy heron.

> **lcjohn said:**
> Hello.
I have a Compaq Presario 1700 laptop with thw following specifications:

P3 700 Mhz
128 MB ram

and I'm wondering if it will run well the newest version of ubuntu?
If it will not run well, then is there another version of ubuntu that my laptop can handle?

Many thanx
LC John

Try running a liveCD first, if that runs then an install should run without a problem. I generally find that 8.04 runs better on older machines than 8.10.

That being said though the minimum requirements for Ubuntu are as follows:

# 300 MHz x86 processor
# 64 MB of system memory (RAM)
# At least 4 GB of disk space (for full installation and swap space)
# VGA graphics card capable of 640x480 resolution
# CD-ROM drive or network card 

The recommended requirements are:

# 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024x768 resolution
# Sound card
# A network or Internet connection

You may need to use the alternate install CD because you may not be able to run the graphical installer. Ubuntu will run, but I doubt it will run well. By that I mean you may not have a Desktop, possibly just command line (anyone ever managed to get a Desktop running with 128MB of RAM?).

I have an IBM thinkpad with 768MB of RAM and a 1.4GHz processor and even it runs 8.04 a little sluggish (the graphics chipset is the weak link there)

---

### Post by lcjohn on 2009-04-22
Thanx for your help, I will try 8.04 and see how it goes

---

### Post by meeples on 2009-04-22
yea if the live disk doesnt work then try Xubuntu its a variant made for lower spec computers:)

---

### Post by porchrat on 2009-04-22
> **lcjohn said:**
> Thanx for your help, I will try 8.10 and see how it goes

I found 8.04 less graphically demanding than 8.10.

Please keep in mind that a new release comes out tomorrow (April 23rd) (jaunty jackalope 9.04).

---

### Post by halitech on 2009-04-22
> **lcjohn said:**
> Hello.
I have a Compaq Presario 1700 laptop with thw following specifications:

P3 700 Mhz
128 MB ram

and I'm wondering if it will run well the newest version of ubuntu?
If it will not run well, then is there another version of ubuntu that my laptop can handle?

Many thanx
LC John

very light on the ram to run any of the "big 3" that is supported. Base install with flux might work better

> **porchrat said:**
> 8.10 is intrepid ibex not hardy heron.



Try running a liveCD first, if that runs then an install should run without a problem. I generally find that 8.04 runs better on older machines than 8.10.

That being said though the minimum requirements for Ubuntu are as follows:

# 300 MHz x86 processor
# 64 MB of system memory (RAM)
# At least 4 GB of disk space (for full installation and swap space)
# VGA graphics card capable of 640x480 resolution
# CD-ROM drive or network card 

The recommended requirements are:

# 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024x768 resolution
# Sound card
# A network or Internet connection

You may need to use the alternate install CD because you may not be able to run the graphical installer. Ubuntu will run, but I doubt it will run well. By that I mean you may not have a Desktop, possibly just command line (anyone ever managed to get a Desktop running with 128MB of RAM?).

I have an IBM thinkpad with 768MB of RAM and a 1.4GHz processor and even it runs 8.04 a little sluggish (the graphics chipset is the weak link there)

actually, from here ( [http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition) ) > System Requirements

Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. 

> **meeples said:**
> yea if the live disk doesnt work then try Xubuntu its a variant made for lower spec computers:)

XFCE is made for lower specs but Xubuntu is not that much lower then Gnome with the way that they pile in gnome apps to get it to work easily.

---

### Post by gn2 on 2009-04-22
The regular Ubuntu CD will be no use to you with 128mb of RAM.
I would suggest downloading an Alternate CD of Xubuntu.

---

### Post by meeples on 2009-04-22
maybe try looking into Damn Small Linux or Puppy LInux? i havent tried them but as far as i know they are made for low spec computers:)

---

### Post by OutOfReach on 2009-04-22
Xubuntu might be a little slow, I recommend either Fluxbox, Crunchbang Linux (Ubuntu-variant with Openbox). Or maybe going down even further into distros like Puppy Linux or DSL

---

### Post by mhh91 on 2009-04-22
Xubuntu is really good for older computers


or Damn Small Linux if you're looking for a non-ubuntu based distro :)

---

### Post by halitech on 2009-04-22
> **meeples said:**
> maybe try looking into Damn Small Linux or Puppy LInux? i havent tried them but as far as i know they are made for low spec computers:)

puppy and DSL are okay to use as a live cd to show things off but I find them not as good as an installed system. I'd look at either a command line install and build up with what they want (no XXXX-desktop stuff) and use XFCE or one of the *box window managers.

---

### Post by boof1988 on 2009-04-22
If you are going to install Ubuntu and you are not able to get any more RAM, then I would recommend the following:
[LIST=1]
[*]Use the [alternative](https://help.ubuntu.com/community/Installation#Installation using the Alternate CD) install disk
[*]Install a lighter-weight desktop environment after you install Ubuntu.  Maybe try [LXDE](http://lxde.org/):

If you have 8.10 or above, you can install [LXDE](http://lxde.org/) by...
```
sudo apt-get install lxde
```

[/LIST]

---

### Post by roger_1960 on 2009-04-22
Hi

Try xubuntu 9.04 (tomorrow!) or, if not fast enough, Puppylinux 4.2 runs really well on lowish spec machines and is really well furnished with applications for such a small distribution.

---

### Post by mark.giblin on 2009-04-22
> **meeples said:**
> maybe try looking into Damn Small Linux or Puppy LInux? i havent tried them but as far as i know they are made for low spec computers:)

All I can say is if you do... be careful with it. Don't know what it did to the first Ubuntu install I put on but I had to wipe the drive, reinstall and then download a gig of installs... Again.

Its not the first time I have encountered an issue with DSL. It appears to be built with little regard for what, if any, operating system already exists. I have had one Windows OS cease to function after using a DSL build, the lappy is a paperweight ATM after running the "LiveCD" version of DSL.

---

### Post by halitech on 2009-04-22
DSL is based on Debian

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

Puppy I'm not sure but I think is based on Debian as well

[http://www.puppylinux.org/home](http://www.puppylinux.org/home)

---

### Post by liamnixon on 2009-04-22
128MB of ram?  You're going to have fun trying to run it.  LXDE or a window manager is the way to go for this, but it's still not too great.  Enlightenment was actually pretty zippy, though (I have a computer with almost the exact same specs as yours).  Don't bother with the normal install, as it will freeze.  You're gonna have to use an [alternate/minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") for it.

Go for it, though!  Maybe you're better at managing your computer than me. ;)

---

### Post by Old_Grey_Wolf on 2009-04-22
> **lcjohn said:**
> Hello.
I have a Compaq Presario 1700 laptop with thw following specifications:

P3 700 Mhz
128 MB ram

and I'm wondering if it will run well the newest version of ubuntu?
If it will not run well, then is there another version of ubuntu that my laptop can handle?

Many thanx
LC John

You need more RAM to run current versions of UBUNTU. 

I think that computer uses a DDR2 SO-DIMM RAM module? Check to see what RAM module it needs. Then PM me. I have a 512MB DDR2 SO-DIMM RAM module I could snail-mail to you.

---

### Post by halitech on 2009-04-22
it should be along the lines of my old Armada M700 which used PC100 so-dimms

[http://en.wikipedia.org/wiki/Compaq_Presario_1700](http://en.wikipedia.org/wiki/Compaq_Presario_1700)

# 600 MHz-1000 MHz Intel Pentium 3 with speedstep,
# 128-512 SODIMM SDRAM PC100
# 6.0 GB-40 GB (6 to 40 billion bytes) Hard drive
# 2x USB 1.1
# 3 hour high-capacity battery
# 24x CD-Rom / 24x CD-RW / 8x DVD-Rom drive
# Mobility Rage M1 AGP Graphics Chip with 8 MB Video RAM

---

### Post by Old_Grey_Wolf on 2009-04-22
> **halitech said:**
> it should be along the lines of my old Armada M700 which used PC100 so-dimms

If it is the PC100 144 pin SO-DIMM then the module I have will not help him.

:(

---

### Post by halitech on 2009-04-22
I've got 2 old laptops that use PC100 144 pin so-dimms and I've searched high and low locally (both are picky on what they will take so not buying from ebay) so I wouldn't hold out much luck on the OP finding any

---

### Post by inxygnuu on 2009-04-22
CrunchbangLinux would work well on a laptop like that

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

:)

---

### Post by dolphin_oracle on 2009-04-22
for those specs, I suggest a distro called Antix.  Its based on debian and mepis, and is specifically for older computers.  antix is a very complete system, with access to the debian repos.  it uses ICEWM by default, but can be set up with lxde or xfce via a meta installer.  It works great on my sony 900mhz duron, 128 mb of ram.

[http://antix.mepis.org](http://antix.mepis.org)

---

### Post by -kg- on 2009-04-22
I have used Puppy Linux, and it is a fine distribution for older computers with limited resources.  128 MB of RAM is adequate to run it.

It has a (approximately) 64 MB footprint and is designed to load into and run totally from RAM.  At the end of the session it will save a file onto your hard drive with your settings and some files (like bookmarks, etc.) and when launched again will load these settings and files to be used in your next session.

It's a fine distro to use to browse the internet with relative safety.  If you run across something that you really wouldn't like to save to your hard drive, you are given the option to not save that session and it will load the previous one on the next reboot.

If at all possible, it would be nice to run Ubuntu, though.  Puppy *is* limited in what you can do with it without a whole lot of trouble (and in some cases, more resources).  Since it runs totally from RAM, though, it runs as fast as your system allows.

---

### Post by egalvan on 2009-04-22
Ubuntu is not Windows...
Puppy is not Ubuntu... 

At times, it's hilarious how similar the arguments are... :P

Let's see...
Puppy has a web browser, word processor, audio player, terminal sessions, cd/dvd burner, file manager, window manager, desktop environment, network connectivity, picture viewer/editor...

No, they are not the exact same versions that run on Ubuntu,
but do you want the same software? 
or similar functions?

Isn't this what we tell Windows users who complain that their favorite piece of software doesn't exist on Linux? :P

And there are "fat" versions of Puppy that have...
FireFox, OpenOffice, the gimp, etc, etc...

You can run it as a LiveCD, or load it to the hard drive, or a USB stick...

Keep your info, or boot clean each time...

With 128M of RAM, it can run totally in RAM

What's not to like? :P

Just remember,
It's Not Ubuntu!
but it's not meant to be! :lolflag:

---

### Post by egalvan on 2009-04-22
Then there is Tiny Core Linux.

A 10meg download....

Yes, TEN MEGABYTES.

Totally mind-boggling what they have squeezed into a mere 10 MegaBytes.

Give it a spin...

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

[I]Tiny Core Linux is a very small (10 MB) minimal Linux Desktop. It is based on Linux 2.6 kernel, Busybox, Tiny X, Fltk, and Jwm. The core runs entirely in ram and boots very quickly.

[/I]

---

### Post by longtom on 2009-04-23
Let me through in [SliTaz](http://www.slitaz.org/en/) - which is my favourite light distro so far.

Really userfriendly and not demanding on resources at all.

---

### Post by mark.giblin on 2009-05-05
If this is any help... 

I have just tried DSL on a Toshiba Laptop, Pentium II 350Mhz, 128MB ram and DSL was a no show.

I went through the motions but it appeared to stall, left it for an hour, still no change.

I remember a time Linux users would boast that Linux will run on anything, well it appears not so.

---

### Post by halitech on 2009-05-06
I've had a few systems that were cranky with any linux distro but would still run windows 2000. I have it running on a Toshiba Tecra (see info in sig) and it would run. DSL I don't find to be all that good to install on a HD and run. A net install of Debian I find is better on low end stuff with either XFCE or LXDE.

What model of laptop is it?

---

### Post by Insanity01 on 2009-05-06
well in school in the linux lessons we use old machines 
and we use ubuntu 8.10 and then trough vmware we run fedora with like 200 +- MB ram put to fedora...So yeah i think ubuntu / fedora should do fine...dunno about openSUSE Tho, always have feeling it's bit less good for older pc's cause it runs slower in general, but that might be me :P

---

### Post by PyroSamurai on 2012-03-20
Okay I personally have a Compaq Presario 1700 Laptop and while AntiX worked on it which is rare, it was too slow. TinyCore worked, installed fast, and worked very fast on the laptop. I will be sticking with it. I have have another old laptop which I will try the other solutions on. None of the ubuntu distros were able to install on the compaq laptop just FYI. They took too much RAM.

---

