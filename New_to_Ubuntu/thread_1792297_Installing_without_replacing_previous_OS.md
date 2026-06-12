---
title: "Installing without replacing previous OS"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by tarshoduze on 2011-06-28
I've seen from a site that the 10.10 release of Ubuntu has a bug in which when you select "Use Entire Partition" or "Use Entire Disk" before installing, the *whole *HD (including the former OS) would be wiped out. Can anyone give me very detailed steps on how to make sure that the Dual-Boot installation will *not* replace my former OS and that it would be successful?

---

### Post by jtarin on 2011-06-28
That's not a bug :P.....what do you think the term means "Use Entire Disk". If you select that it will use the entire desk....on the otherhand if you will select a partition it will use that entire partition. There is nothing ambiguous about this. Pretty straightforward. What is that you don't understand?

> Can anyone give me very detailed steps on how to make sure that the Dual-Boot installation will not replace my former OS and that it would be successful?Have you setup a dual boot before? Then 10.10 is no different.
You need detailed steps on setting up a dual boot or detailed steps on a guaranteed dual boot?

---

### Post by wolfen69 on 2011-06-28
That's not a bug that it would wipe out your other OS. "use entire disk" means just that. How can it use the whole disk without wiping out the previous OS? But during install you can select "install side by side" with your existing OS. I've never had it fail me.

---

### Post by amjjawad on 2011-06-28
> **tarshoduze said:**
> [SIZE=3]Can anyone give me very detailed steps on how to make sure that the Dual-Boot installation will *not* replace my former OS and that it would be successful?[/SIZE]

Check my signature.
The guide is talking about Ubuntu 10.04. Try to understand the general concept and I'm sure you'll figure out how to do it with Ubuntu 10.10.

I couldn't update the guide because I had some health problems and couldn't even login to this forum. Hopefully some other time I'll do that :)

---

### Post by jtarin on 2011-06-28
> **amjjawad said:**
> Check my signature.I think he's got you with the "sucessful" bit. :lolflag:

---

### Post by tarshoduze on 2011-06-28
> **jtarin said:**
> That's not a bug :P.....what do you think the term means "Use Entire Disk". If you select that it will use the entire desk....on the otherhand if you will select a partition it will use that entire partition. There is nothing ambiguous about this. Pretty straightforward. What is that you don't understand?

Have you setup a dual boot before? Then 10.10 is no different.
You need detailed steps on setting up a dual boot or detailed steps on a guaranteed dual boot?
Well, uh, both. I already installed Ubuntu 10.10 on a computer, but I didn't dual-boot. It was successful. But I have to do a dual-boot sometime so I'd appreciate it if I could be assured that what I'm doing will result in a flawless dual-boot. I'd go with the automatic partitioning. So, what buttons do I press from the start 'till it starts installing a successful dual-boot?

---

### Post by nzjethro on 2011-06-28
I used [this guide,]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") and found it very useful, and have now got Windows 7 and Ubuntu working together "successfully".

Not sure what Windows you are working with, but I imagine that if it's not 7 it'd work just as well. Of course, anything that you wouldn't like lost should be backed-up before you begin your dual-boot setup.

If you have any issues with dual booting, post here, and we can help you out.

---

### Post by jtarin on 2011-06-28
> **tarshoduze said:**
> Well, uh, both. I already installed Ubuntu 10.10 on a computer, but I didn't dual-boot. It was successful. But I have to do a dual-boot sometime so I'd appreciate it if I could be assured that what I'm doing will result in a flawless dual-boot. I'd go with the automatic partitioning. So, what buttons do I press from the start 'till it starts installing a successful dual-boot?

[Here]("http://members.iinet.net.au/~herman546/p24.html")
and
[Here.....]("http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/")

I can't guarantee you a flawless dual boot.....that's up to you.

---

### Post by grahammechanical on 2011-06-28
I have seen some advice to defrag the drive using a Windows utility and to then partition the drive using a windows utility and to tell Ubuntu to install into those created partitions.

From what others have posted I would suggest that defragging the drive in Windows is most important. It reduces the risk of loosing data when the drive is partitioned and the data is moved.

Regards.

---

### Post by Mark Phelps on 2011-06-28
The MOST important step is to use the Win7 Disk Management utility to shrink the Win7 OS partition -- and then leave the new space unallocated.  Allowing the installer to shrink the partition runs the risk of filesystem corruption in Win7.

And BEFORE you do anything else, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  This will come in handy later if you need to repair the boot loader.

---

### Post by Rob the Techie on 2011-07-01
I found a really helpful guide with info on a couple different methods [here]("http://www.howtowindows.com/how-to-windows-guides/running-ubuntu-and-windows-at-the-same-time/"). Hope it helps!

---

