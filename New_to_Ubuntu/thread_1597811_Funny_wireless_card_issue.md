---
title: "Funny wireless card issue?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Poincare101 on 2010-10-15
I recently built a new computer and I installed ubuntu on it. I have installed a dlink dwa 556 ( [http://www.dlink.com/products/?pid=549](http://www.dlink.com/products/?pid=549) ) wireless card. It is (according to madwifi-project.org) a AR5418 based card. AFAIK, this should work out of the box right? Well, it doesn't. It doesn't even show up in lspci. What's going on?! I also tried doing "sudo modprobe ath9k", but it still doesn't work!

---

### Post by hhh on 2010-10-15
Maybe something in this thread...
[http://ubuntuforums.org/showthread.php?t=718244](http://ubuntuforums.org/showthread.php?t=718244)

---

### Post by Poincare101 on 2010-10-15
Yeah, I checked that and the madwifi svn is no longer active. I don't really know where else to get the madwifi sources...
Besides, the card IS atheros based, so why is there so much trouble with this?

Also, the card's light is blinking, I contacted dlink and they said this means that the card is communicating with the motherboard correctly. I wonder why its not showing up in lspci...

EDIT: Check this out: [http://wireless.kernel.org/en/users/Drivers/ath9k/devices](http://wireless.kernel.org/en/users/Drivers/ath9k/devices)
The dlink dwa 556 is listed. Still not working?!

---

### Post by hhh on 2010-10-15
> **Poincare101 said:**
> EDIT: Check this out: [http://wireless.kernel.org/en/users/Drivers/ath9k/devices](http://wireless.kernel.org/en/users/Drivers/ath9k/devices)
The dlink dwa 556 is listed. Still not working?!
The first thing that page says is that it is horribly out of date.

I found a Linux Mint forum post from just over a year ago where someone said they had success using these instructions...
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

Here's the thread...
[http://forums.linuxmint.com/viewtopic.php?f=53&t=10209](http://forums.linuxmint.com/viewtopic.php?f=53&t=10209)

Unfortunately, everything I'm finding on Google is pretty out of date, for example these links...
[http://brainstorm.ubuntu.com/item/6589/](http://brainstorm.ubuntu.com/item/6589/)
[http://brainstorm.ubuntu.com/idea/11585/](http://brainstorm.ubuntu.com/idea/11585/)

This might be your best option (even though it's an old solution)...
[http://jbopensrc.wordpress.com/2007/12/03/quickfix-ar5418-with-ndiswrapper/](http://jbopensrc.wordpress.com/2007/12/03/quickfix-ar5418-with-ndiswrapper/)

---

### Post by Poincare101 on 2010-10-15
Yeah, ndiswrapper STILL doesn't fix it. There's a red exclamation mark where the wireless signal should be.

---

### Post by jtarin on 2010-10-16
> **Poincare101 said:**
> Yeah, I checked that and the madwifi svn is no longer active. I don't really know where else to get the madwifi sources...
[SourceForge]("http://sourceforge.net/projects/madwifi/files/madwifi/0.9.4/madwifi-0.9.4.tar.gz/download")....where else. :)

---

### Post by Poincare101 on 2010-10-16
I cannot build the module since I don't have a configured kernel source ...

---

### Post by jtarin on 2010-10-16
From the install file.
> The driver is built using the Linux kernel build mechanism.  This means
you must have some part of the kernel source distribution installed on
the machine where you want to build the driver.  In particular, the
kernel include files, makefiles, build scripts and configuration must be
available.

[B][I]This will be present if you built your kernel from source.  Otherwise
you may need to install an additional kernel development package from
your distribution that would match your kernel.  For example, the
development package for the default kernel is called linux-headers on
Debian and kernel-devel on Fedora Core.  Installing a package with full
kernel sources should not be generally necessary.[/I][/B]

---

### Post by macem29 on 2010-10-16
what ubuntu version you using? I'm at 10.04 and my Atheros adapter is a pain, madwifi kind of solved it...
it was pointed out to me that 10.10 has native Atheros support in the kernel though I haven't tried it

---

