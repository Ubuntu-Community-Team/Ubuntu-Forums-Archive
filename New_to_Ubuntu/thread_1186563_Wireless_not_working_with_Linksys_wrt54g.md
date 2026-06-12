---
title: "Wireless not working with Linksys wrt54g"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Xorlan on 2009-06-13
Hi folks!

  I'm very new to using ubuntu, and very beginner with anything Linux.  Only know as much as how to navigate around the terminal prompt, piping commands, greping, etc.

Anyhow, I'm banging my head against the wall currently with a wireless problem, and I'm hoping someone might be able to offer some insight.  First off, here's the setup and known factors that I know.

Computer:  EeePC 1000 "netbook", running Ubuntu 9.04 juanty "netbook remix".

Router: Linksys WRT54G V8, with latest updated firmware I could find (8.00.6).  Just updated it the other day.

Anyhow, here is the situation.  The wireless card WILL connect to my router, but the speed is so ungodly slow that it's just not usable.  I tried pinging various known ips, such as google and what not and the response times were pitiful.  

Now, if I go to my school, I can hop on the wireless just fine.  I found another un-secured router in my local area (a motorola), connected, and it worked just perfectly.  Speeds were great.  My computer REFUSES to work with this linksys though.  

If I do a hardwire connection straight into the router w/ CAT5, my netbook works perfectly.  It's just the wireless connection. 

I've spent countless hours scouring these forums in hopes to find a solution, and so far the only thing I've really dug up is an IPv6 issue.  So, the solution was to disable it, but apparently it's coded into the Kernel in 9.04 and the only solution to "disable" it is to recompile the entire kernel.....far above my actual skill in this OS.  

I'm beginning to think it's not actually an IPv6 problem though, since my computer apparently works with every other wireless device, other than my own.  If this is a router settings problem, I just haven't been able to find the answer on what needs to be changed.  

Any input would be much appreciated on this issue.  I'll be happy to run any sort of test needed and post the results, etc.  I'm very determined to break free from the chains of Microsoft, and so far, this issue is severly making me want to turn away....though I won't!

Nutshell summary:

Netbook won't work with my linksys router, though functions perfectly with any other sort of wireless. 

Works with a direct connection via ethernet cable.

My windows based machines are having no problem with this router.

---

### Post by ajgreeny on 2009-06-13
I don't think you need to recompile the kernel just to disable ipv6 system-wide, I'm sure there is a way to do it either in the router configuration or with a config file edit in ubuntu, though as windows runs properly, I suspect it is a ubuntu config problem.

Have a look here and see if it is possible also in jaunty.:
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

---

### Post by synapsys on 2009-06-13
I know this sounds too easy.... but have you tried changing the channel that your wireless router is using? Maybe all your neighbors  are using the same channel you are using and clogging up the air waves.....just a thought....

---

### Post by Xorlan on 2009-06-13
Don't think it's the channel, though it's worth a shot.  Currently I'm sitting on my desktop and the wireless is perfectly fine, though my netbook refuses to work wirelessly on my router. :(

---

### Post by synapsys on 2009-06-13
> My windows based machines are having no problem with this router

Missed that part.....

What wireless chipset are you using?
What driver are you using?

---

### Post by Xorlan on 2009-06-13
> **synapsys said:**
> Missed that part.....

What wireless chipset are you using?
What driver are you using?

Well, assuming "hardware drivers" is the right place to go to check this....

I'm apparently currently using the free "ath5k" driver that came along with the installation of ubuntu.  I have an option to switch to an alternate atheros "madwifi" driver, which is proprietary.  I tried that, rebooted, and then the wireless wasn't even showing up at all (as in, not even an option, or was greyed out).

---

### Post by synapsys on 2009-06-13
Please post 

```
lspci | grep Wireless
```

and contents of 

> /etc/modprobe.d/blacklist

---

### Post by Xorlan on 2009-06-13
So checking my connection information for my Linksys, it says my speed is listed as 1 Mb/sec.  The motoral router I can connect to is listed as 6 Mb/s.  Not sure if this is the issue, as you'd think even with a 1 Mb/s speed the wireless would still work fine...
If this is the issue, I'm not really sure how to change this.

---

### Post by Xorlan on 2009-06-13
> **synapsys said:**
> Please post 

```
lspci | grep Wireless
```and contents of

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


cat: /etc/modprobe.d/blacklist: No such file or directory

---

### Post by synapsys on 2009-06-13
My bad blacklist.conf

P.S. I'm using ath5k driver for AR242x chipsets on several laptops running jaunty 9.04.... could possibly have something to do with netbook remix configuration.

---

### Post by Xorlan on 2009-06-13
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by Xorlan on 2009-06-13
Bump for any other sort of input, and to help myself from not ripping my hair out :)

---

### Post by synapsys on 2009-06-13
What encryption are you using?

---

### Post by Xorlan on 2009-06-13
Well, for the purposes of actually figuring out this problem, I completely reset my router and disabled my security.  Desktop is running just peachy on vista, but this problem still persists.

I read somewhere that the pre-installed networm manager that comes w/ ubuntu can have issues or something with a wrt54g, and currently have Wicd manager.  Still the exact same problem.  

I feel like it's a problem on my router, even though my desktop is currently running just peachy off of it.  Only reason why I say that is because this ubuntu netbook picks up other wireless signals and works just fine.  Though, I have absolutely zero clue as to where to begin trying different things on the router.

---

### Post by Xorlan on 2009-06-13
Sort've fed up with this whole thing, so I'm just going to re-install ubuntu again and pray that magic happens.

---

### Post by Xorlan on 2009-06-13
no magic :(

---

