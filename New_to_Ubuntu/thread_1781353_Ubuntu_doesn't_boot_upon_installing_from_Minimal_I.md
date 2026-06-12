---
title: "Ubuntu doesn't boot upon installing from Minimal Install"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by faviouz on 2011-06-13
Hi,

I am attempting to install Ubuntu from the [Minimal Install]("https://help.ubuntu.com/community/Installation/MinimalCD"). For that, I downloaded the [latest version's 64 bit of the Minimal Install]("http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-amd64/current/images/netboot/mini.iso") and put it in a USB device by using Unetbootin. I booted the computer from the USB device, and at the splash menu I selected Command-line-install. From there, I just entered the information as requested and followed the steps very carefully. When the installation was finished and it asked me to remove all the installation media, I removed the USB device and waited for the computer to reboot. But nothing showed up, just an infinite blinking underscore. I could not type anything or get rid of it at all.

I tried literally everything. I tried not removing the USB device at the end, I tried lots of different setups during install, I tried not choosing Command-line-install at the splash menu. I even burned the Minimal Install ISO image to a CD and tried to install from it, but that didn't work either. However, in this case, when rebooting, it didn't show the infinite blinking underscore. It kind of looked like the system was booting, but at one point the monitor went black. Not the regular black screen though, it's like the monitor was disabled and no light was emitting from it. I could not type or do anything at this point either.

After being able to boot, I was going to [install the lubuntu-desktop package]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall"), because I like LXDE. And if it matters, I want the 64 bit version because my laptop can't handle Minecraft in Linux operating systems unless it's a 64 bit version. Even then, I still need to install the real ATI graphics drivers.

By the way, I have tried other distribution's Minimal Install and they work. But I can't get Ubuntu's Minimal Install to boot after installing. What are your thoughts? Thanks in advance!

---

### Post by gmargo on 2011-06-13
Try hitting "Alt-F1".

I usually install a command line version to start, but somewhere in the default startup stuff, the virtual console gets switched to "Alt-F7" in preparation for graphics.  So try an ALT-F1 combination to switch to virtual console #1.

---

### Post by faviouz on 2011-06-13
Hi gmargo, thanks for replying!

When should I hit Alt-F1? And should I install from the CD or a USB device?

---

### Post by CowzRule on 2011-06-13
> **faviouz said:**
> Hi gmargo, thanks for replying!

When should I hit Alt-F1? And should I install from the CD or a USB device?

I believe you'd want to hit "Alt-F1" when you see that blinking underscore.

---

### Post by gmargo on 2011-06-13
> 
It kind of looked like the system was booting, but at one point the  monitor went black. Not the regular black screen though, it's like the  monitor was disabled and no light was emitting from it.
From your description above it sounds like the machine is booting.  When that monitor goes black, you should hit the ALT-F1 combo (ALT-F1 through ALT-F6 should show login prompts.)

---

### Post by faviouz on 2011-06-13
Thanks for the guidance guys!

I will be trying this immediately.

---

### Post by faviouz on 2011-06-13
Thank you, pressing Alt-F1 did the job and I was able to install lubuntu-desktop afterwards. My Ubuntu installation is working fine now, much appreciated! :)

---

