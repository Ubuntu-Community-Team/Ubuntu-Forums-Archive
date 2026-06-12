---
title: "a non-bloated system?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by stevepoppers on 2010-06-14
I use so few of the packages that come installed by default in ubuntu. 4 of the accessories, none of the games, one of the image things, none of the stuff that's not even in the main menu by default. Can I install Ubuntu without all this extra crap and pick what I want after install?

Are these programs just part of Gnome?

A little googling tells me that simple things like aptitude, wget, vi(m), and whois can be missing if I install the meta-package, ubuntu-minimal instead of ubuntu-standard. I don't know how to make that switch, anyway, but I might like to.

I guess this scratches the surface of a bigger question of the things installed on my computer by Ubuntu:
What components are Ubuntu?
What components are Gnome?
What components are plain Linux?

I want a very basic system, without any extra bloat, but with the ability to install any bloat I choose. This is a big reason I quit Windows.

---

### Post by bodhi.zazen on 2010-06-14
Yes.

I almost never do a default install these days, use the minimal CD and build up.

There is a learning curve, but it is easier then removing things.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by snowpine on 2010-06-14
Hi Steve, 

You can remove any applications you don't use with the Software Center (or the Synaptic Package Manager, terminal commands, etc.) You can also install Ubuntu from scratch, choosing only the packages you want, by using the Minimal Install CD: 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I have to disagree with your characterization of Ubuntu as "bloated." The full Ubuntu install (including the operating system, office suite, media players, games, etc.) fits on a single CD and occupies less than 0.4% of a typical 1TB hard drive.

---

### Post by DaGarver on 2010-06-14
[This]("http://web2linux.com/minimal-ubuntu-lucid-setup/") guide will help you set up a Lucid minimal install. It really doesn't take that much work, from what I can see.

---

### Post by philinux on 2010-06-14
Lucid minimal install, then install lxde.

Or peppermint. [http://peppermintos.com/](http://peppermintos.com/)

---

### Post by Bachstelze on 2010-06-14
Just wanted to say that while a "cli" install from a Minimal or Alternate CD is probably what you want, you can go even smaller if needed by using debootstrap, with an installation process similar to Gentoo (minus the compiling).

---

### Post by stevepoppers on 2010-06-14
Ok, I found [this]("http://ubuntuforums.org/showthread.php?t=1155961&page=6") thread by finally googling the right thing and finding a lifehacker article. Can the same thing be done with a server disk? I have a few laying around.

What do you test all these different distros on? I don't want to have to trash my working desktop every time I hear about some cool new one or something. Spare computers, possibly with multiple partitions? Or maybe most of you have much better resources than I.

Oh, and as for it being "bloated", it's definitely not like Windows, but it's still more than I need/want. So, for me, yes, it is kinda bloated. I just hate the extra junk. I'm really excited to be able to install this way now.

---

### Post by philinux on 2010-06-14
> **stevepoppers said:**
> Ok, I found [this]("http://ubuntuforums.org/showthread.php?t=1155961&page=6") thread by finally googling the right thing and finding a lifehacker article. Can the same thing be done with a server disk? I have a few laying around.

What do you test all these different distros on? I don't want to have to trash my working desktop every time I hear about some cool new one or something. Spare computers, possibly with multiple partitions? Or maybe most of you have much better resources than I.

Oh, and as for it being "bloated", it's definitely not like Windows, but it's still more than I need/want. So, for me, yes, it is kinda bloated. I just hate the extra junk. I'm really excited to be able to install this way now.

Virtualbox. [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Chesamo on 2010-06-14
What you're asking for is the type of thing I work on.

[http://ubuntu-minimal-desktop.blogspot.com/](http://ubuntu-minimal-desktop.blogspot.com/)

It takes the command-line installation and builds up, only giving you what you ask for and a few needed utilities.

---

### Post by stevepoppers on 2010-06-14
> **philinux said:**
> Virtualbox. [http://www.virtualbox.org/](http://www.virtualbox.org/)

Please tell me it works better than the live cd. That's about all I need to know, lol.

---

### Post by CharlesA on 2010-06-14
> **stevepoppers said:**
> Please tell me it works better than the live cd. That's about all I need to know, lol.

It would normally work better, yes.

---

### Post by snowpine on 2010-06-14
> **stevepoppers said:**
> Please tell me it works better than the live cd. That's about all I need to know, lol.

What's wrong with the Live CD?

---

### Post by QIII on 2010-06-14
Philinux and I seem both to extol the virtues of virtualization in harmony...

I don't dual boot at all any more.  I virtualize everything.

However, if I want to test something, for instance a particular video driver, I might temporarily install something on a separate hard drive to dual boot it, check what I want and get rid of the installation when I am done.

Virtualization has the one drawback of forcing the use of the virtual machine's virtual hardware, so bear that in mind.  If you are not specifically interested in testing some technical bit (like a driver for a particular hardware component), I think virtualization is the way to go.  

No need to shut down one OS to get back to GRUB and restart another.  In VirtualBox, you can even save the state of the virtual machine and have it turn right back on where you left it.  You can also create a snapshot so that if something unexpected happens as you fiddle around, you can go back to where it was working and reconsider what you just did that disappointed you.

---

### Post by QIII on 2010-06-14
> **snowpine said:**
> What's wrong with the Live CD?

It's slower.

But I guess as long as someone knows that, they can look past that and not assume that the OS is inherently sluggish.

---

### Post by waynefoutz on 2010-06-14
The problem with testing a Linux distro or any other OS in Virtualbox is that it won't tell you if the hardware in your machine will work or not. If the host system is connected to the internet, then the client OS will be too. But that isn't going to tell you if your wireless is going to work if you install it. 

VirtualBox is nice though, I use it and have a few virtual machines, including Win XP and Android OS, that I like to play around with. It is a fast and easy way of checking out an OS before you even burn it, to see if you like the interface or not.

---

### Post by stevepoppers on 2010-06-15
> **stevepoppers said:**
> Can the same thing be done with a server disk?

I think this is all the more I need right now. I've installed crunchbang and there are still a bunch of things that I won't use, but maybe I'll try them out for now. I'm going to try to build my own and make it similar to crunchbang. I just want to know if I can use the server disk I have lying around to get the base system.

Virtualbox didn't go well for me. Everything I tried to install on it broke somehow. I'm working with Dell Dimension 2400 that someone was going to trash, so I've got something to play on for now.

---

### Post by snowpine on 2010-06-15
There is no reason to do an Ubuntu Server install unless you are actually running a server. Use the Minimal CD as I suggested above if you want a bare-bones Ubuntu install. :)

---

### Post by stevepoppers on 2010-06-15
I figured I could save myself a download.

Thanks all!

---

### Post by bodhi.zazen on 2010-06-15
> **stevepoppers said:**
> I figured I could save myself a download.

Thanks all!

Did you see the size of the minimal iso ? It is 10 mb , less then the server kernel and updates you would use if you installed from the server iso.

---

### Post by Bachstelze on 2010-06-15
> **bodhi.zazen said:**
> Did you see the size of the minimal iso ? It is 10 mb , less then the server kernel and updates you would use if you installed from the server iso.

10 MB, plus all the packages. ;) If one already has an Alternate or Server ISO, better do a minimal install from that, and then download only the updates, instead of downloading all the packages.

---

### Post by bodhi.zazen on 2010-06-15
> **Bachstelze said:**
> 10 MB, plus all the packages. ;) If one already has an Alternate or Server ISO, better do a minimal install from that, and then download only the updates, instead of downloading all the packages.

True, but it depends on the age of the iso, what you say may be true of 10.04 for the moment (I am not sure how many upgrades there are from a fresh install).

In addition, most of the packages the OP wants (gnome) are not on the server iso ...

---

