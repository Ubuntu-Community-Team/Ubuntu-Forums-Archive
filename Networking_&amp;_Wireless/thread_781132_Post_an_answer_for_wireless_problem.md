---
title: "Post an answer for wireless problem"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Nosolution05 on 2008-05-04
I'm running Ubuntu 8.04 and hit the brick wall trying to connect to the the internet.  As seen I'm not the only one with this problem so I'm asking: can someone please take the time to write an understandable, coherent, straight-forward solution for all of us alike stuck in the same boat?

Been searching endlessly for 3 days, read all the stickies, each one with a different solution with a high level of complexity.

Thanks in advance for you time

---

### Post by CleverJake on 2008-05-04
What is the brick wall you have hit?
can you see any networks and not connect to them?
can you see nothing at all?
can you not get a driver to work?

---

### Post by Nosolution05 on 2008-05-04
can't connect to wireless network, I dont even see wireless networks available

---

### Post by CleverJake on 2008-05-04
what is your wireless card?
have you attempted to install any drivers?

---

### Post by sardus76 on 2008-05-04
hi cleverjake!
im in the same situation of nosolution05...
how do i get the driver for the wireless thingy?
ive got an acer aspire 5050, but in the website doesnt say anything about wireless drivers! its so fustrating!!
hope u can help us!

thanks!

---

### Post by q1u2i3z on 2008-05-04
hi 
i have a linksys i can see the networks but cannot connect.i dont know if i even have the drivers installed. running 8.04
could us the help thanks steve

---

### Post by sardus76 on 2008-05-04
n

---

### Post by dm6257 on 2008-05-04
Another voice in the wilderness.  I am running 8.04 with a Linksys WUSB54G wireless adapter.  I can connect to my wireless network but that's where things stop. No internet.  No DNS. No DHCPOFFERS.

Thanks,
Dale

---

### Post by Ayuthia on 2008-05-04
Can those with wireless problems post their lspci -nn (if it is a wireless card) or lsusb (for USB wireless).  Here are a couple of card options and I am still looking for others:


Broadcom Cards:
You can start here [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
It will give you an option on an easy way which uses the native driver and another one that leads you to the NDISwrapper route which has a lot of steps but more people seem satisfied with this option.

Atheros 5007:
You can try this: [http://ubuntuforums.org/showthread.php?t=771527](http://ubuntuforums.org/showthread.php?t=771527)
I don't have it, so I can't tell you how well it works.

---

### Post by ugm6hr on 2008-05-04
> **Ayuthia said:**
> Can those with wireless problems post their lspci -nn (if it is a wireless card) or lsusb (for USB wireless).  Here are a couple of card options and I am still looking for others:


Indeed.  Please provide information for us to help you.

The outputs from the above commands, in addition to this one (capital C):
```
lshw -C network
```

Those others again:
```
lspci
lsusb
```

And, if you are half-way there:
```
iwlist scan
```

Most importantly, can each user **start a fresh thread** with the outputs of all these (and any other relevant details about what has been tried already).

---

### Post by ugm6hr on 2008-05-04
Indeed.  Please provide information for us to help you.

The outputs from the above commands, in addition to this one (capital C):
```
lshw -C network
```

Those others again:
```
lspci
lsusb
```

And, if you are half-way there:
```
iwlist scan
```

Most importantly, can each user **start a fresh thread** with the outputs of all these (and any other relevant details about what has been tried already).

As for the OP request for a generic How-to - there is no such thing, since it is highly dependent on what wifi device you use.

If you are searching for a solution - use the above commands to identify the hardware you have, then google the exact hardware:

e.g. my lspci:
```
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```
So I would search for AR2413.

Also - one specific place to search for this is the ndiswrapper site: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

Then at least you can provide some details if it still doesn't work.

---

