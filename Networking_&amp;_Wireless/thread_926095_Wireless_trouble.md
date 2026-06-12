---
title: "Wireless trouble"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Icyyrobe on 2008-09-21
Hello all,

I've had Ubuntu for some days now and these past days the internet worked on wireless... but today I can only find:

Wired Connection
Point to point connection...

And of all the FAQ's I've been reading these hours noone could give me an answer...

So If anyone got an idea of what this might be please reply...

PS: This is in "Network settings"-> "Connections".


-Icyyrobe

---

### Post by Crafty Kisses on 2008-09-21
That's strange, post the results of this command:
```
lshw -C network
iwconfig
```

---

### Post by Icyyrobe on 2008-09-21
Hello and thanks for the reply!

Where shall I put that command?
I just started using Ubuntu so I don't know anything about the OS.

-Icyyrobe

---

### Post by Icyyrobe on 2008-09-22
Could someone tell me? 

Thanks,

-Icyyrobe

---

### Post by Crafty Kisses on 2008-09-22
You want to put that command in the Terminal.

---

### Post by Redptc on 2008-09-22
To find a terminal go to Applications>accessories>Terminal...Wait for a second.......type in command and press enter


....better still.....use 'cut & paste'!

---

### Post by Icyyrobe on 2008-09-30
robert@lappytoppy:~$ lshw -C network iwconfig
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


This showed up, I can't use the internet on the laptop, since I can't find the wireless connection thingy anymore...
So I used my memory pen to transfer this.

---

### Post by Icyyrobe on 2008-10-28
Please!

I've been waiting for a long time now!

Someone will help me soon?

---

### Post by Icyyrobe on 2008-10-28
Bump

---

### Post by Ayuthia on 2008-10-28
> **Icyyrobe said:**
> robert@lappytoppy:~$ lshw -C network iwconfig
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


This showed up, I can't use the internet on the laptop, since I can't find the wireless connection thingy anymore...
So I used my memory pen to transfer this.
lshw -C network is one command and ifconfig is the second command.  You cannot have them togeter.

---

