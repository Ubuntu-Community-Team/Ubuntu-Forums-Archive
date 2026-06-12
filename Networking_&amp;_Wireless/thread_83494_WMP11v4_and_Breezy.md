---
title: "WMP11v4 and Breezy"
date: 2005-10-28
forum: Networking &amp; Wireless
---

### Post by abbeyroadd on 2005-10-28
First off this is my first post, I have been reading the forums for some time now but I need some help now and everyone here seems to be very knowledgeable here.

I am quite new to the Linux world and after a lot of research I decided that Ubuntu 5.10 (for AMD 64 CPU's) would be the best place to start.  I guess my research fell short when I tried to get online with my wireless card.  I just installed Ubuntu 5.10 on my home PC (dual boot with WinXP) and I am having a problem getting it to "use" my wireless PCI card, it's a Linkysys WMP11 version 4 that is giving me a pretty large headache.

I spent about an hour and a half last night talking with a friend (who has helped me a great deal so far) and we couldn't get the OS to utilize my card.

If I go into Device Manager I see that it recognizes my card, I loaded all three of the drivers (downloaded the most up to date drivers from Linksys' website) using ndiswrapper (ndiswrapper -utils), which I installed from my install CD using Synaptic.

What I did was:

```

ndiswrapper -i "driver name.inf"
modprobe -r ndiswrapper
modprobe ndiswrapper
```

I did this for all three of the drivers, and if I do an *ndiswrapper -l* it says:

```

lsbcmnds     driver present
lsipnds      driver present, hardware present
wmp11nds     driver present
```

But when I do an *iwconfig* it says:

```

lo No wireless extensions
eth0 No wireless extensions
sit0 No wireless extensions
```

The last thing I did was:

```
echo ndiswrapper >> /etc/modules
```

I am sure I have done this all correctly, anyone have any ideas?  BTW this is my kernel info:

```
2.6.12-9-amd64-generic
```

Please help me!!!

- Derik

PS, I have read almost every thread on here but none of them seemed to work.

:(

---

### Post by abbeyroadd on 2005-10-29
:(

---

### Post by abbeyroadd on 2005-10-30
I also asked this question on [www.linuxquestions.org](www.linuxquestions.org) and someone had me do an *ndiswrapper -m* which returned:

```
modprobe config already contains alias directive
```

Anyone have any ideas about this?

---

