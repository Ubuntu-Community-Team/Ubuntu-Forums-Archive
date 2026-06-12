---
title: "Boot is broken"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by ratwhowouldbeking on 2009-04-29
Hi everyone,

Ubuntu is acting really strangely - as in, I can't boot into it.
I wrote to a file on a previous installation in an attempt to stop the keychain from asking for my password when I logged on (I want the wireless to open on its own without requiring passwords from me).  I copied and pasted something to a file in /etc/pam.d from a user on these forums from some time ago.  Next time I booted Ubuntu, it got past the OS loading screen and then I got a black screen with some pixelated green and red lines at the top.  Okay, so I broke it, whatever - at this point I'm used to doing re-installs of Ubuntu. 
So I re-installed 8.10 (the only disk I have) and upgraded to 9.04, got everything up and running smoothly, then I turned it off for the night... and turned it on this morning, and back to the strange black screen of death.  But this time I didn't do anything, I swear!
Any ideas how I can fix this?

GNU/Linux hates me.  :(

---

### Post by northern lights on 2009-04-29
What's your monitor's native resolution?

What graphics device do you have?

Can you please post the output of ```
sudo lshw -C dosplay
``` (boot into Recovery Mode, drop to a root shell).

---

### Post by ratwhowouldbeking on 2009-04-29
When I do that, it flashes
```
PCI (sysfs)
```
and sends me back to prompt.

Assuming the above was a typo of "display", the output I get is (hopefully I won't make a typo transcribing, if something doesn't make sense that might be why):

```

*-display:0 UNCLAIMED
description: VGA compatible controller
product: RV570 [Radeon X1950 Pro]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:02:00.0
version: 9a
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: RV570 [Radeon X1950 Pro] (secondary)
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@0000:02:00.1
version: 9a
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress bus_master cap_list
configuration: latency=0

```

I should also note that I am currently using the 32-bit architecture of Ubuntu, but the initial problem occurred when I was using 64-bit architecture, so I don't think that has anything to do with the issue.

---

### Post by northern lights on 2009-04-29
From the shell, run```
sudo apt-get update && sudo apt-get install xorg-driver-fglrx
```

---

### Post by ratwhowouldbeking on 2009-04-29
Can't do that, I don't have a wired connection to my internet - router is across the room.  No idea how to work my wireless card in shell (and even if I did, my wireless card doesn't get along swimmingly with Ubuntu at the best of times).
I appreciate the help, but I think I'll do a clean wipe of the partition and try once more.  Thank you!

---

### Post by ratwhowouldbeking on 2009-04-30
I did a completely clean install, and updated the above driver as you detailed.  Still the same problem at reboot.

It's not there initially - it isn't a problem until I download updates.

---

### Post by handydan918 on 2009-04-30
> **ratwhowouldbeking said:**
> I did a completely clean install, and updated the above driver as you detailed.  Still the same problem at reboot.

It's not there initially - it isn't a problem until I download updates.

RTEminds me of the old gag about the guy who says to his doctor;
"Doc, it hurts when I do this."
Doc says..."Well, don't do that!"

If there is no compelling reason to move up from 8.10...
DON'T!

---

### Post by northern lights on 2009-05-02
> **handydan918 said:**
> RTEminds me of the old gag about the guy who says to his doctor;
"Doc, it hurts when I do this."
Doc says..."Well, don't do that!"

If there is no compelling reason to move up from 8.10...
DON'T!
Quite some truth in that.

Although something that worked in a previous release should keep being functional in the next also.

All your base are belong to us!

---

