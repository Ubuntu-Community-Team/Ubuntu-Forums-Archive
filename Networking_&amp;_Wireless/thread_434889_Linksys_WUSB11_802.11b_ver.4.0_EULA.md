---
title: "Linksys WUSB11 802.11b ver.4.0 EU/LA"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by stooker on 2007-05-06
I understand there are many threads on this, that's where I lost track. After some googling I found this:

*"I use linux alot and the newer versions of WUSb11(v4 and v3) don't seem to have linux drivers yet (ndis wrappers are not working for me with v4). This situation will most likely be resolved when new drivers are written, as is always the case with linux."*

Does this mean that I'm in a shitty situation (cause I have the 4.0 version) and have to buy an older version of this adapter?

I've seen sollutions on Kubuntu and Ubuntu forums, but they were most of the time for 2.5/2.6 or 2.8. But no concrete sollutions for 4.0. 

Can anybody help me out here. In the mean time I'll keep on googling and reading, but I hope  somebody here can get me out of missery.

Thanks !

---

### Post by stooker on 2007-05-07
nobody?

---

### Post by n00b@linux on 2007-05-07
Try running 'lsusb -vs 003:004' (without the 'sudo' this time).  Hopefully, it should show lots of detail about the USB device plugged into USB port #4 and running over USB #3 (ie. the same USB port you plugged it into when you originally ran 'lsusb').

If that doesn't work, just run 'lsusb -v' and you'll get HEAPS of output.  Please don't post it all to this thread - just post the part that deals with your wireless USB adapter.  

BTW, we're trying to get more information about the chipset in your wireless USB adapter and '-v' option for 'lsusb' means 'verbose', ie. lots of detail.

Ik ben niet nederlandse, btw.

---

### Post by stooker on 2007-05-07
The first code gives nothing, just an <enter>

The second code gives a lot, but only shows the HP printer, and a lot of free USB slots.

It looks look the computer doesn't detect the hardware.

ps. Belg ?

---

### Post by stooker on 2007-05-07
hmm...starting to think the damn thing is broke, I have to test it on another machine.

I read somewhere that some versions have a AMD chipset, they just don't work here and others have an Intel chipset and they work out-of-the-box.

---

### Post by n00b@linux on 2007-05-07
Yes, test it on another machine (or under windoze) to make sure the thing actually works!

It's quite possible (albeit unlikely) that it's not recognised by the kernel.  One way to test this is to run the 'dmesg' command immediately after inserting the USB stick into the USB port.  It should report if it's been recognised or not.  You only need to see the last few lines so rather than run the full 'dmesg' command, you can run 'dmesg | tail' which will show you just the last few lines.  You can do either one, it doesn't really matter.  What's important is that the lines show that the device has been recognised.  Typically this will mean you'll see the name and chipset of the device in the output.

---

