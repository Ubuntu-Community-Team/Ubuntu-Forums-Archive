---
title: "Does Ubuntu need to be shut down like Windows?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by MehdizLinux on 2009-11-19
I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble?

---

### Post by philinux on 2009-11-19
Some people only turn their machines off and reboot twice a year. I use hibernate a lot.

---

### Post by Jon Monreal on 2009-11-19
> **MehdizLinux said:**
> I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble?

Not exactly sure what you mean.

Many would argue that turning of a Windows machine is unnecessary. Likewise, others would tell you that it is good to to turn it off in order to save power. In the end, it really depends on what you're doing with your computer, not what OS its running. [Take a look here for more information]("http://computer.howstuffworks.com/question328.htm").

---

### Post by Redmage913 on 2009-11-19
Are you asking if you need to do through the proper shutdown procedure or if you can just cut the power or hold in the power button for however many seconds it takes?

---

### Post by SuperSonic4 on 2009-11-19
> **MehdizLinux said:**
> I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble?

Not really but it will help your power consumption if you do. After all servers are designed with ideally infinite uptime (but in reality they go down about once in a million)

---

### Post by philinux on 2009-11-19
> **MehdizLinux said:**
> I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble?

Yes it needs to be shutdown properly. Using the power button can cause the system not to boot.

If ever you get a system freeze up use this.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

---

### Post by coffeecat on 2009-11-19
> **MehdizLinux said:**
> I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble?

Do you mean just switching the power off or pulling the plug without doing a graceful shutdown? If you do, you risk corrupting the filesystem - just as with Windows. This is *usually* repairable, but try not to do it.

---

### Post by scorp123 on 2009-11-19
> **MehdizLinux said:**
> I was wondering that Ubuntu needs to be shut down each and every time and turning the machine off may cause trouble? All modern operating systems --even stupid Windoze-- are quite complex these days and have a ton of config files open all the time. So yes, you should _ALWAYS_ use the proper shutdown procedure when you turn off your computer. Because if you don't you might cause corruptions to those files that were open ... 

Ubuntu has journalling file systems and some other mechanisms that should help to prevent trouble. But still ... you shouldn't force it.

If you have a reasonably modern PC (post 2004) then it should be aware of its power button. Means: If you press your power button once very gently your system should realise that you want it to power down ...

With my systems this works. So this would also be a method that might work.

---

### Post by ivanvajar on 2009-11-19
Well, let me see... Yup! Even stupid DOS had to be taken back to C:\> before turning computer off.

---

### Post by qrwe on 2009-11-19
> **philinux said:**
> Some people only turn their machines off and reboot twice a year. I use hibernate a lot.

"Suspend" is very often used by me. Works fine and saves some power too.

---

### Post by wojox on 2009-11-19
I reboot for kernel upgrades, that's about it. Other than that I have no idea what you mean.

---

### Post by blur xc on 2009-11-19
> **ivanvajar said:**
> Well, let me see... Yup! Even stupid DOS had to be taken back to C:\> before turning computer off.

I remember those days, oh how simple.  cd c:\,  run "park" to park the hard disk heads, and then just flip the power switch on the back of the pc...  Funny that back then when it was normal to shut down via. the power switch, it was on the back of the case, and now that it's a no-no, case manufacturers put the button on the front.

I might have a fuzzy memory of there being a reset button on the front of my old 286 though, but that was more than half my lifetime ago...

BM

---

### Post by necromonger on 2009-11-19
A proper shut down will help you pay your power bill. mine never runs when I am in the bed or away from home.

---

### Post by MehdizLinux on 2009-11-19
Thanks for replies. Suspend doesn't work for me. I found similar posts with hundred suspend fail reports. I found no solution yet. If I suspend, after pressing the power button (to bring the machine back to work) screen goes black for ever and hard disk light keeps on! Upgraded the NVIDIA driver, the same... By the way I cannot see the driver version but I'm sure It's upgraded:

```

*-display
                description: VGA compatible controller
                product: G71 [Quadro FX 1500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e1000000-e1ffffff memory:d0000000-dfffffff(prefetchable) memory:e2000000-e2ffffff ioport:1000(size=128) memory:e0000000-e001ffff(prefetchable)


```

---

### Post by scorp123 on 2009-11-19
> **MehdizLinux said:**
>  Suspend doesn't work for me. I found similar posts with hundred suspend fail reports. I found no solution yet. If I suspend, after pressing the power button (to bring the machine back to work) screen goes black for ever  Because when you suspended, the "nvidia" driver got unloaded from memory.

So you have to tell your system not to unload the "nvidia" driver. Enter this into a terminal:

```
gksudo gedit /etc/default/acpi-support
```

This should have opened a config file regarding ACPI support. Find the line that says .... :

```
 ...
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""
... 
```

Change it so it now reads like this:

```
...
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=**[COLOR="Red"]"nvidia"[/COLOR]**
... 

```

Save the file. Then reboot. Voila. Done. After that your Nvidia card should come back to life after a suspend.

---

### Post by MehdizLinux on 2009-11-19
> **scorp123 said:**
> Because when you suspended, the "nvidia" driver got unloaded from memory.

So you have to tell your system not to unload the "nvidia" driver. Enter this into a terminal:

```
gksudo gedit /etc/default/acpi-support
```

This should have opened a config file regarding ACPI support. Find the line that says .... :

```
 ...
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""
... 
```

Change it so it now reads like this:

```
...
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=**[COLOR="Red"]"nvidia"[/COLOR]**
... 

```

Save the file. Then reboot. Voila. Done. After that your Nvidia card should come back to life after a suspend.
Well Scorp... Didn't work... When I power on the screen flashes in a sec with a small command runing and then goes off. I mean the monitor goes to power saving mode! And as I said the hard disk light keeps on which seems ridiculous to me! and I have to reset the machine. Don't think it's graphic card driver issue.

---

### Post by scorp123 on 2009-11-19
> **MehdizLinux said:**
> When I power on the screen flashes in a sec with a small command runing and then goes off. I mean the monitor goes to power saving mode!  And if we disable that too? You sometimes have to play with those parameters ... For my old Samsung P50 laptop which has a Nvidia card too I use these parameters (same config file as before):

```

... 

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="nvidia"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=platform

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

...
```

---

### Post by Chris Edgell on 2009-11-19
What IS the difference between suspend and hibernate?

What is the difference between log out and shut down?

---

### Post by Miljet on 2009-11-19
As I understand it, suspend saves your current configuration to memory. The memory is kept alive and all other peripherals shut down. Hibernate saves your current configuration to disk and shuts everything down, including memory.

When you log out, the computer is still available for other users. And of course when you shut down, the computer is powered down.

---

### Post by Chris Edgell on 2009-11-19
This shed a lot of light.  One of my advisors told me "Just leave it on."  The other one told me, "Just hit the power button to turn it off, it doesn't matter, and it doesn't hurt."  Now I'm really wondering if I should hibernate all during the day and shut down at night.  Sounds right??  Or maybe, like Philinux, mostly hibernate then I'm thinking we probably shut down if we're going to be gone any amount of days.

---

### Post by Bios Element on 2009-11-19
> **Chris Edgell said:**
> This shed a lot of light.  One of my advisors told me "Just leave it on."  The other one told me, "Just hit the power button to turn it off, it doesn't matter, and it doesn't hurt."  Now I'm really wondering if I should hibernate all during the day and shut down at night.  Sounds right??  Or maybe, like Philinux, mostly hibernate then I'm thinking we probably shut down if we're going to be gone any amount of days.

It should be noted that pressing and released the power button will send a signal for ubuntu to shutdown. Pressing and holding will kill the power and instantly shutdown the system. The risk in doing so is of course data loss...and a borked system.

---

### Post by Jon Monreal on 2009-11-19
> **Chris Edgell said:**
> This shed a lot of light.  One of my advisors told me "Just leave it on."  The other one told me, "Just hit the power button to turn it off, it doesn't matter, and it doesn't hurt."  Now I'm really wondering if I should hibernate all during the day and shut down at night.  Sounds right??  Or maybe, like Philinux, mostly hibernate then I'm thinking we probably shut down if we're going to be gone any amount of days.

Then you run into the argument that hibernating puts undue stress on the disk because the contents of your RAM are dumped to your HDD. Personally, I put my laptop into sleep mode if I'm going to be using it again soon and shut down otherwise. For desktops, I leave them on during the day (running F@H) and turn them off at night.

---

### Post by Chris Edgell on 2009-11-19
Thanks.

So what is "sleep mode"?  Suspend?

---

### Post by Jon Monreal on 2009-11-19
> **Chris Edgell said:**
> Thanks.

So what is "sleep mode"?  Suspend?

[They are synonymous]("http://en.wikipedia.org/wiki/Sleep_mode").

---

### Post by scorp123 on 2009-11-20
> **Chris Edgell said:**
>  So what is "sleep mode"?  Suspend? Yes. And best thing is: there are several levels of "sleep". Just like with humans. Humans have "REM sleep", "alpha wave sleep", and what not.

So laptops have e.g. "S1 sleep", "S2 sleep" and the more desirable "S3 sleep". 

[http://www.lifsoft.com/power/faq.htm](http://www.lifsoft.com/power/faq.htm)

"S4 sleep" is the same as hibernation.

So laptops that can only achieve S1 and S2 are not really "sleeping" at all, they are just running in an extremely reduced power-consumption mode. Such a laptop can maybe last a few hours that way, but eventually it will drain its batteries.

"S3 sleep" is more desirable and all modern laptops (post 2003) should be able to achieve it. In that state everything but the RAM chips is powered off. A laptop in such a state can survive several days without being recharged.

"S4 sleep" is hibernation. A laptop writes all its RAM contents onto a part of the harddisk. On Linux the "Swap" partition is used for this. Hence why your "Swap" partition should at least be 1.5 times the size of RAM so swap information + the RAM contents could fit in there if you were ever to need to hibernate your laptop. A laptop that his hibernating is essentially powered off and should not use any power from its batteries. It should be able to survive several years in that state. When you power it on again it should read all the memory contents from the harddisk again and after a few seconds of heavy disk activity it should be back into the state it had before you hibernated it.

---

