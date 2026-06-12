---
title: "Hot swapping hard drives while in the OS"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by taylortots275 on 2011-02-25
I was curious to see if there was a quick terminal command to detect hard drives attached directly to the motherboard. I recently installed Ubuntu 10.04 on a spare machine at my work to do data transfers with. It would be rather tedious to continually restart every time we need to detect another hard drive. This machine does not have an internet connection so I can't fetch any external packages (or at least I don't want the break down the station to move it just yet).

Thanks in advance
Taylor

---

### Post by jim Kane on 2011-02-25
> **taylortots275 said:**
> I was curious to see if there was a quick terminal command to detect hard drives attached directly to the motherboard. I recently installed Ubuntu 10.04 on a spare machine at my work to do data transfers with. It would be rather tedious to continually restart every time we need to detect another hard drive. This machine does not have an internet connection so I can't fetch any external packages (or at least I don't want the break down the station to move it just yet).

Thanks in advance
Taylor

could you not use a ide/sata to usb adaptor
or have i misunderstood what you need to do..

mike

---

### Post by taylortots275 on 2011-02-25
Sure, but internal SATA connection would be faster. 

I have the side of my machine taken off so I have direct access to the SATA ports on the motherboard. Whenever I need to do a data transfer, I simply connect the drive to one of the SATA cables and power. Ubuntu doesn't auto-detect the hard drive when it is plugged in directly to the motherboard. I was wondering if there was a terminal command to detect new hard drives and mount the it without restarting the computer.

---

### Post by Paqman on 2011-02-25
> **taylortots275 said:**
> Ubuntu doesn't auto-detect the hard drive when it is plugged in directly to the motherboard.

It should do. Make sure you plug in the data cable before the power one. Might be worth checking your BIOS settings, too.

---

### Post by Trevster on 2011-02-25
To detect the new drive run fdisk as root.
 ```
sudo fdisk -l
```

You will have to mount the harddrive manually. [https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")

---

### Post by taylortots275 on 2011-02-26
Excellent advise, I'll try one or all of them in the morning when I head back into work.

tb

---

