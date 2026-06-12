---
title: "64 bit clean install... network card not seen"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by Multi-Booter on 2007-10-12
First off... I love that 'auto search' feature that shows you related threads before you post... Unfortunately none of those helped... I searched pretty hard first.

Anyways, here is the deal... I installed Kubuntu (LTS) on my Dell XPS 410.
It was the best linux install I have encountered yet.
Pretty smooth cosidering (I gave up on Fedora by core 6)

Nothing works exactly as it should, but everything is functional with default drivers. The exception is my ethernet card (no wireless involved). 

I'm not a beginner at linux, but I am still very much a novice with the hardware issues, etc. So I went and tried to get the card working. Trouble is that Kubuntu doesn't even see it.

This dell has an onboard adapter, so I don't even know where to begin... other than try to figure out what stuff I need to get for my board... which MAY be found on dell.com somewhere... I dunno...

So where do I start here guys?

And should I be posting in the dell section or am I in the right place?

Thanks in advance.

---

### Post by Multi-Booter on 2007-10-13
Nobody have a clue?

---

### Post by kevdog on 2007-10-13
Most likely have to use ndiswrapper with this one with the 64 bit windows xp drivers for your card (if there are any).

If you post
lspci -nn
lshw -C network

that should give us a start.  Sometimes 64 bit drivers are hard to come by -- not Vista drivers.

---

### Post by Multi-Booter on 2007-10-14
> **kevdog said:**
> Most likely have to use ndiswrapper with this one with the 64 bit windows xp drivers for your card (if there are any).

If you post
lspci -nn
lshw -C network

that should give us a start.  Sometimes 64 bit drivers are hard to come by -- not Vista drivers.

Here is what I got from that...

[COLOR="Blue"]0000:00:00.0 0600: 8086:29a0 (rev 02)
0000:00:01.0 0604: 8086:29a1 (rev 02)
0000:00:19.0 0200: 8086:104b (rev 02)
0000:00:1a.0 0c03: 8086:2834 (rev 02)
0000:00:1a.1 0c03: 8086:2835 (rev 02)
0000:00:1a.7 0c03: 8086:283a (rev 02)
0000:00:1b.0 0403: 8086:284b (rev 02)
0000:00:1c.0 0604: 8086:283f (rev 02)
0000:00:1c.4 0604: 8086:2847 (rev 02)
0000:00:1d.0 0c03: 8086:2830 (rev 02)
0000:00:1d.1 0c03: 8086:2831 (rev 02)
0000:00:1d.2 0c03: 8086:2832 (rev 02)
0000:00:1d.7 0c03: 8086:2836 (rev 02)
0000:00:1e.0 0604: 8086:244e (rev f2)
0000:00:1f.0 0601: 8086:2812 (rev 02)
0000:00:1f.2 0104: 8086:2822 (rev 02)
0000:00:1f.3 0c05: 8086:283e (rev 02)
0000:01:00.0 0300: 1002:7183
0000:01:00.1 0380: 1002:71a3


  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dffe0000-dfffffff iomemory:dffdb000-dffdbfff ioport:ecc0-ecdf irq:10[/COLOR]

---

### Post by Multi-Booter on 2007-10-16
Anyone?

---

### Post by noob12 on 2007-10-17
This puppy:
```

0000:00:19.0 0200: 8086:104b (rev 02)

```
is your wired Ethernet controller.   In Feisty it is covered by the e1000 driver.

In Dapper, I think you would need to build it.

ADDED:
But let's makes sure
```

modinfo e1000

```
See if there is a line that looks like this:
```

alias:          pci:[COLOR="Green"]v00008086d0000104B[/COLOR]sv*sd*bc*sc*i*

```
You'll see many similar lines, but look for one with the 104B.  If it is not there you need to build the driver.  If it is there, the driver should cover it but it is having some problems claiming the device, and you will find more (hopefully) if you look at the output of **dmesg** soon after booting.

---

### Post by Multi-Booter on 2007-10-19
> **noob12 said:**
> This puppy:
```

0000:00:19.0 0200: 8086:104b (rev 02)

```
is your wired Ethernet controller.   In Feisty it is covered by the e1000 driver.

In Dapper, I think you would need to build it.

ADDED:
But let's makes sure
```

modinfo e1000

```
See if there is a line that looks like this:
```

alias:          pci:[COLOR="Green"]v00008086d0000104B[/COLOR]sv*sd*bc*sc*i*

```
You'll see many similar lines, but look for one with the 104B.  If it is not there you need to build the driver.  If it is there, the driver should cover it but it is having some problems claiming the device, and you will find more (hopefully) if you look at the output of **dmesg** soon after booting.

OK, I didn't get anywhere with the above.

I do have my dmesg output though...

Could anything contained in all that output help?

---

### Post by noob12 on 2007-10-19
If you have no specific need to stay on Dapper, you might want to upgrade to Feisty.

For Dapper, you should download and build the driver.

---

### Post by Multi-Booter on 2007-10-19
What about just wiping it out and going to 7.10?

---

### Post by noob12 on 2007-10-19
Not having made the move to Gutsy yet myself, I'm not in a position to recommend it.  Why don't you try out the Gutsy (7.10) LiveCD and see how that works for you?  You can make a much more informed decision that way.

---

### Post by Multi-Booter on 2007-10-21
Well, I didn't get an email notification that you had answered, so I didn't return to the forums.

Instead, I spent some time downloading a couple 64 bit versions of the 7.10.

I'm pleased to report that Ubuntu 7.10 appears to be working.
In fact, I'm posting this while booted to the Live CD.

> ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
  


How about that.....

---

