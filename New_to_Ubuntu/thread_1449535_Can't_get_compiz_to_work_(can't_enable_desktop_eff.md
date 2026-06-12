---
title: "Can't get compiz to work (can't enable desktop effects)...help?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by doctorbighands on 2010-04-07
Hi there,

I got my hands on an older laptop to use as a kitchen PC for my wife. I just installed Jaunty, and everything's going well, except I can't enable desktop effects.

When I type "compiz" into the terminal, it says something about "xgl: not present". I've read elsewhere that I might need to install a package called xserver-xgl, but it apparently isn't in the repos for Jaunty.

Here is the relevant information from lshw:
```

*-display UNCLAIMED
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 13
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4

```

Here is what my xorg.conf looks like. I suspect this might be part of the problem:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I have no idea what else to do. Any help here is appreciated!

---

### Post by northern lights on 2010-04-08
Your video card is running under the minimalistic default driver and does hence not support hardware acceleration. You can verify this by running```
glxinfo | grep direct
```

I'm not too certain an S3 Savage can even do what you want it too. Don't quote me on that, though.

---

### Post by doctorbighands on 2010-04-08
Well, I know that there's a driver out there for the S3 Savage. I installed the xserver-xorg-video-savage package in Synaptic; how I get the kernel to use the driver in that package?

---

### Post by doctorbighands on 2010-04-08
bump!

---

