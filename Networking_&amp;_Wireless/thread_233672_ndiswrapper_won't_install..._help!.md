---
title: "ndiswrapper won't install... help!"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by samma on 2006-08-10
I just got dapper set up on my computer to dual-boot with windows.  Everything worked fine except for my wireless networking.  I downloaded ndiswrapper but I don't know ho to install it. I know there are other tutorials on this, but being the complete noob I am, I can't figure them out. :confused:
Please help me!

---

### Post by varean on 2006-08-11
To install ndiswrapper:
```
tar -xvzpf ndiswrapper-*
cd ndiswrapper-*
make install
```

Then, check to see if your card is supported:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

If it is, great, get the driver for it (.inf file) and then
```
ndiswrapper -i /path/to/driver.inf
```

If it isn't supported(like mine was) check to see if it came with a CD, if it did, chances are installing the drivers on the CD(ndiswrapper -i /path/to/driver.inf)might get it to work.

Then, one ndiswrapper -l says "driver name hardware present, driver present" then 
```
modprobe ndiswrapper
ehco "ndiswrapper" >> /etc/modules.autload.d/kernel-2.6
```

Note that the modprobe and echo commands need to be run as root/superuser.

---

### Post by roachk71 on 2006-08-11
[LEFT]I believe the first question should be: "Exactly what brand, model and revision (or version) of card do you own?"

Secondly, if your card isn't based on a supported chipset out-of-the-box, the _latest_ version of ndiswrapper must be built from source.

That option requires building a custom kernel as well, since the wrapper will need modules from that build... Even I wish the developers could make it simpler than that, since building a custom kernel takes anywhere from 45 minutes to a few hours, depending on your computer's CPU, storage type and speed, etc. (Several factors go into that.)

Oh, and I'd almost completely forgotten about this: If you're willing to do that, you'll need to set the kernel configuration up for your architecture (CPU brand and type, features) before compilation. I'll cover this in subsequent posts.

Let me know what model card you have, and I'll look up the kernel build information, if that's what you're going to need. 
[/LEFT]

---

### Post by samma on 2006-08-11
I am using Linksys WUSB54G

---

### Post by samma on 2006-08-11
I tried to install it with the make command, but apparantly the terminal doesn't recognize that command.:confused:

---

### Post by roachk71 on 2006-08-11
[LEFT]In that case, you probably don't have the build tools installed.

The following packages need to be installed before you can use Make:[LIST]
[*]build-essential
[*]gcc (the compiler collection)
[*]linux-headers (version-specific)
[*]and you might want to install linux-image for your CPU.[/LIST]There are several versions of linux-image, each for different CPUs (386 for older computers, 686 for modern [Pentium or Celeron], and k7 for the latest AMD CPUs.)

Synaptic can be used to install all of these packages, and dependencies should be resolved automatically. Let me know how everything goes.
 [/LEFT]

---

### Post by samma on 2006-08-11
Ok, I'll try that.

---

### Post by samma on 2006-08-11
can you point me to which linux-header version I should download?

---

### Post by roachk71 on 2006-08-11
[LEFT]First, we need to find out what kernel you're using. To do this, open a terminal window and type:

```
uname -a
```
This command (there are other options, this one the most verbose) tells you about the kernel version and architecture on the left, and the maximum kernel your machine can handle on the right, along with the OS name.
[/LEFT]

---

### Post by samma on 2006-08-11
OK, this is my kernal version: 2.16.15.23-386

---

### Post by roachk71 on 2006-08-11
[LEFT]The version displayed is also the version of the headers you need.

Also, I should mention that for my computer, the only solution that works like a charm is compiling a vanilla kernel from kernel.org, along with the latest ndiswrapper, which can be found here:

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

This is the most reliable way to go.

If everything easy won't work (compiling the wrapper without source,) and you're willing to take the time-consuming approach, I can assist with that. 

[/LEFT]

---

### Post by az on 2006-08-11
If you installed using the desktop cd, ndiswrapper-utila is on a repo on that disk, apart from the live session.  You rarely need to recompile ndiswrapper.

Boot into your installed ubuntu and insert the Desktop cd again.  The package manager will start and you will then be able to install ndiswrapper-utils.

Then set up your card.

sudo ndiswrapper -i driver.inf


If the card hasa native linux driver, you will need to prevent it from being loaded automatically (blacklist it) if you want to use ndiswrapper.

---

### Post by roachk71 on 2006-08-11
[LEFT]Thanks, Azz.

I should have remembered that option, as well. :-k
[/LEFT]

---

### Post by samma on 2006-08-13
what name do I blacklist if I'm using WUSB54G version 1? eth1? or something else?

---

