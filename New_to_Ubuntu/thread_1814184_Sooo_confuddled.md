---
title: "Sooo confuddled"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by o15977 on 2011-07-29
please help

Q.1 Are all kinds of device drivers included in the filesystem after all installation?
if not, does the Live CD has all the drivers?

Q.2 are there devices that doesn't support 32bit? or all device has drivers for both 32-bit and 64-bit?

---

### Post by sadaruwan12 on 2011-07-29
> **o15977 said:**
> please help

Q.1 Are all kinds of device drivers included in the filesystem after all installation?
if not, does the Live CD has all the drivers?

Q.2 are there devices that doesn't support 32bit? or all device has drivers for both 32-bit and 64-bit?

Little bit confusing but here I go.

Q.1 Yes all the drivers in other word hardware are detected and applies the correct functioning methods except for propitiatory drivers mostly VGA drivers are not installed by default but the a driver manager window will ask you if you want install them or not and if you want to you can install them.

Q.2 Well, 99.9% of the devices are supported in any 32-bit or 64-bit version so theres no issue to worry about.

But if you tell us what you really want to know we could be more helpful to you.

---

### Post by Paqman on 2011-07-29
> **o15977 said:**
> 
Q.1 Are all kinds of device drivers included in the filesystem after all installation?
if not, does the Live CD has all the drivers?


There are a lot of drivers included in the kernel, yes. However, not everything. Common exceptions include AMD and Nvidia graphics cards, and some wifi chips.

The LiveCD has all the drivers a freshly installed copy of Ubuntu would have. Once installed you can also use the Hardware Drivers tool to get the additional drivers you need for the stuff I mentioned above. Generally speaking, almost all hardware is very easy to get running on Linux these days.

> 
Q.2 are there devices that doesn't support 32bit? or all device has drivers for both 32-bit and 64-bit?

Support for 32-bit and 64-bit is exactly the same. I've never run into any hardware that only has one or the other.

---

### Post by o15977 on 2011-07-29
> **sadaruwan12 said:**
> Little bit confusing but here I go.

Q.1 Yes all the drivers in other word hardware are detected and applies the correct functioning methods except for propitiatory drivers mostly VGA drivers are not installed by default but the a driver manager window will ask you if you want install them or not and if you want to you can install them.

Q.2 Well, 99.9% of the devices are supported in any 32-bit or 64-bit version so theres no issue to worry about.

But if you tell us what you really want to know we could be more helpful to you.

Thanks a lot for the help!
can you recommend software that copies entire drive but not like dd which will give a file as big as the entire drive?
I'm intending to move my entire system to a flash drive, so it flies. can you also recommend a easy synchronising software?

---

### Post by o15977 on 2011-07-29
> **Paqman said:**
> There are a lot of drivers included in the kernel, yes. However, not everything. Common exceptions include AMD and Nvidia graphics cards, and some wifi chips.

The LiveCD has all the drivers a freshly installed copy of Ubuntu would have. Once installed you can also use the Hardware Drivers tool to get the additional drivers you need for the stuff I mentioned above. Generally speaking, almost all hardware is very easy to get running on Linux these days.



Support for 32-bit and 64-bit is exactly the same. I've never run into any hardware that only has one or the other.

Thanks a lot for the help!
can you recommend software that copies entire drive but not like dd which will give a file as big as the entire drive?
I'm intending to move my entire system to a flash drive, so it flies. can you also recommend a easy synchronising software?

---

### Post by Paqman on 2011-07-29
> **o15977 said:**
> Thanks a lot for the help!
can you recommend software that copies entire drive but not like dd which will give a file as big as the entire drive?
I'm intending to move my entire system to a flash drive, so it flies. can you also recommend a easy synchronising software?

[Clonezilla]("http://clonezilla.org/")

---

### Post by Mark Phelps on 2011-07-29
> **o15977 said:**
> ... I'm intending to move my entire system to a flash drive, so it flies. 

Don't be surprised if it does not "fly"!

Flash drive memory is a LOT slower than typical system memory, so it's more likely your system will be slower, not faster.

---

### Post by aeiah on 2011-07-29
> **Mark Phelps said:**
> Don't be surprised if it does not "fly"!

Flash drive memory is a LOT slower than typical system memory, so it's more likely your system will be slower, not faster.

if we're talking about a usb stick, yes, its usually slow than typical hard drives. if we're talking about SSDs, their speed ranges from slightly faster to a lot faster (technical terms).

---

