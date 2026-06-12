---
title: "howto set two RAID mirrored HDD in Ubuntu"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by soricel_z on 2008-06-04
I am new in Ubuntu. I have got a Fasttrack TX2000 (Promise Technology) RAID controller and I can not set Ubuntu to see two HDD as one - as a Mirror! (I allready set them to be mirrored from the controller bios, but UBUNTU sees them as two separate disks). Can you provide help please ?  Robert

---

### Post by SpaceTeddy on 2008-06-04
i'd say wrong forum - this is networking and wireless.

Regardless of that, you probably have a Raid-enabled controller, not a raid controller itself. If Ubuntu sees the two devices, then the controller does not support real raid but is only supporting it. I'd put my money on some intel matrix storage device. 

And here comes the flaw - i don't know anything about it :(

sorry

---

### Post by soricel_z on 2008-06-04
> **SpaceTeddy said:**
> i'd say wrong forum - this is networking and wireless.

Regardless of that, you probably have a Raid-enabled controller, not a raid controller itself. If Ubuntu sees the two devices, then the controller does not support real raid but is only supporting it. I'd put my money on some intel matrix storage device. 

And here comes the flaw - i don't know anything about it :(

sorry

Thank you very much. 
1. Yes I am about to learn about the forums, sorry about wrong forum.
2. Probablly you are right. Anyway at Promise Technology I fond support and utilities only for Suse  or Redhat ...... I am not that good to adapt them to Ubuntu...
Thanks,
Robert

---

### Post by SpaceTeddy on 2008-06-04
i've toyed with these things once - and found that, if your hw-controller does not do the job for you, you really want to use mdadm (the Linux tools for software raid). they are sophisticated and work flawlessly (for me at least) even if they are not nearly as easy as hw-controllers.

cheers :)

---

### Post by kevdog on 2008-06-04
3-ware RAID controllers are truly hardware RAID controllers, rather than software RAID.  Many are Ubuntu/Debian specific as listed on their website.

---

