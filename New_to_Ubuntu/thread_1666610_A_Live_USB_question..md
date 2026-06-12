---
title: "A Live USB question."
date: 2011-01-13
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-01-13
I have a question about using Live USBs.  Today I tried a Linux distro (not Ubuntu) as a Live USB using Startup Disk Creator.

For example, the distro requires a 400 MHz Processor and 128 MB RAM.  I put it on my laptop, works fine, but when I put it on a 2.0 GHz, 512 MB RAM computer, it freezes up or takes a long time (I'm not sure which).

So I just want to know what kind of a computer would handle it?  I can use it just fine on my laptop, I just wondered why it's so slow a computer that should be able to handle the OS.  Please answer as I'm new to using a Live USB and thanks.

By the way, the 2.0 GHz computer runs Ubuntu 10.04 just fine.  I believe that Ubuntu is more powerful than a distro that uses a 400 MHz processor.

---

### Post by wojox on 2011-01-13
Startup Disk Creator only copies Ubuntu distro's. :confused:

---

### Post by LinuxFox on 2011-01-13
> **wojox said:**
> Startup Disk Creator only copies Ubuntu distro's. :confused:Really, then it must be the distro I was playing around with.  Sometimes when a distro catches my attention, I like checking out the Live CD.  The Live CD also had Startup Disk Creator.  That's what I was using, though I did try it with Ubuntu the other day, only to get that slow/freezing result on the same machine.

---

### Post by wojox on 2011-01-13
Maybe the graphics card/chip? Do you know the model?

---

### Post by LinuxFox on 2011-01-13
> **wojox said:**
> Maybe the graphics card/chip? Do you know the model?Not really, I think it's an on-board graphics chip.  I know my Laptop has an Intel 965.  Just mentioning it to see if there's a difference.

---

### Post by darkhelmetchris on 2011-01-13
I wouldn't really call myself an expert, but I would call myself "seasoned."  I've installed Ubuntu, plus a few other distros, I'm guessing somewhere between 100 and 200 times over the last 6 years.  It's just fun.

To your problem... Sometimes its necessary to supply kernel parameters (such as noapic, acpi=on/off/force, vga=normal, ...and so on).  With this in mind, I would suggest a quick search about running the particular distro of Linux on the type of hardware you have and see if others have suggested kernel parameters for that situation.

I notice that you mention the Intel 965 graphics on your laptop, and in my experience that's been quite stable with Ubuntu.  I have noticed that some of the more recent Intel graphics revisions do require kernel parameters to function properly.  For example, Ubuntu 9.10 with Intel GMA4500M graphics often requires the kernel parameter i915.modeset=0 in order to provide any noticeable video at all; your mileage may vary.

So have a look at possible kernel parameters for your hardware and distro combination.  That's my 2 cents worth.

---

### Post by mastablasta on 2011-01-14
another option is that the distro that works on older computer uses an older kernel that is not so compatible with newer processors/disk and such.

---

### Post by LinuxFox on 2011-01-14
Thanks darkhelmetchris and mastablasta for the answer.  I wouldn't say I know much about kernels, but if that's the problem, then I won't use the Live USB on that machine.  I'll just use the Live USB on my laptop then.

Thank you for answering.

---

