---
title: "wireless working in Feisty (intel 3945)"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by dracomordag on 2007-07-27
alright, my wireless was not working with a fresh install of feisty, so i decided to go straight to the source and download the driver from the intel official site.

in its readme, it said > Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net).  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.2.16.tgz
	% cd ieee80211-1.2.16
	% make 
	# make install   <--- You may need to be root
	% cd ..
when following these steps, it made me append IEEE80211_IGNORE_DUPLICATE=y during the make step

anyway, now when i go to the next step (cd ipw3945-1.2.0 ; make) it spits out the same error message about appending IEEE80211_IGNORE_DUPLICATE=y, then when i do append that, it says ```
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.20-16-generic/include/ /lib/modules/2.6.20-16-generic/

You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1

```


what the hell is going on?



PS: i know that the 3945 should be supported out of the box with Feisty... why wasn't it? is it because my computer came with a "kill switch" (a switch on the front of the laptop that lets you turn wireless capability on or off manually)?

what am i suppoed to do? i fear i severely messed up my kernel

---

### Post by dracomordag on 2007-07-27
also, 

lspci
```
06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)

```

lspci -n
```
06:00.0 0280: 8086:4229 (rev 61)

```

lspci -vvd 8086:4229```

06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

```

sudo modprobe ipw3945
```
2007-07-27 22:00:44: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```

---

### Post by dracomordag on 2007-07-27
anyone?

---

### Post by linux23dragon on 2007-07-28
> **dracomordag said:**
> anyone?

Hi 

The ieee80211 subsystem you had built had changed the Kernel Symbols and I think the Kernel Configure options too. 

Apart from recompileing the kernel, I have no idea how to reverse these changes.  

But you have not broken your kernel modules AFAIK.

To be sure, you can reinstall all kernel modules (using Synaptic) and the Graphics card driver (using Envy) and then reboot.

Keep in mind that you will now always see this warning message:

```

WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
```So if you don't like that idea, then you might need to reinstall Ubuntu.  I don't know how to reverse the Kernel Symbols, without recompiling the kernel.

If you still want to try to compile the drivers, then don't let ieee80211 change anything.

Question.

Are you sure you don't already have this driver installed by default?

---

