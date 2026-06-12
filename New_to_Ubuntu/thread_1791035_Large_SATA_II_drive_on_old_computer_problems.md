---
title: "Large SATA II drive on old computer problems"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by MysticMetal on 2011-06-26
Problem:  I'm having difficulties using my brand new 2TB WD SATA II HDD in my old desktop

trial 1:  I hooked it up and tried it
result:  bios didn't see it.  When I tried to search for ide drives my bios locked up
research:  it turns out my bios is old, and I simply can't use my hard drive on the motherboard SATA II slots.

trial 2:  I left the drive in the computer and hooked up the front of a SATAII enclosure interface to it (SATA II to USB to make externals from internals), cut a hole in a strip in the back and ran a usb cable from the interface into a  usb port on the back of my computer.
result:  no good; ubuntu can't do squat with it.
research:  I think that the current ubuntu may not handle the size of the drive, but I've read the WD page some and it seams that there is built in support for these drives in th kernel (I'm still to new to fully understand this so please excuse any self proclamation of ignorance there)

trial 3:  I used the usb interface to connect it to  my newer netbook
result: wasn't able to use it

thought:  maybe I can't use it because I haven't formatted it yet
thought: how the heck can I format it if I can't use it?

question:  If I buy a new SATA II card for my desktop will that interpret the drive nicely for my bios?  I think I saw something like this but can't seem to find it again.

sorry about tall the colons

---

### Post by ian dobson on 2011-06-26
Hi,

Linux has no problems with large drives (I have 7 2Tb drives in my server). Your problem is the BIOS, it it can't find the drive/crashes then try a BIOS update. 

If you add a PCI SATA card to your computer abd the card has it's own BIOS then it should work, just make sire the chip used is compatible with linux.

Regards
Ian Dobson

---

### Post by SchindlerShadow on 2011-06-26
you can format the drive using the app called "Disk Utility" in ubuntu. if all else fails, you can buy a sata to ide converter on the cheap. ubuntu can recognize a drive many times bigger than that one btw

---

### Post by crispy_420 on 2011-06-26
As mentioned earlier, I would go with the expansion card option to take it out of the BIOS hands. I don't know if the onboard BIOS is required as I have not had this issue so I can't comment of this factor.

---

### Post by MysticMetal on 2011-06-26
Ok thanks everyone I'll go with the pci card then.

---

### Post by mastablasta on 2011-06-27
if motherboard has SATA plug in why the BIOS doesn't recognise it? is it because the disk is SATA2? Anothe roption (if it is possible ) would be to upgrade BIOS. this is not alwys a possibility, but when it is it should be an easy enough task to do.

---

### Post by MysticMetal on 2011-06-28
Yeah, it turns out that my motherboard has SATA sockets, but my drive is SATAII.  So I've ordered a card (that reputably works in fedora, so I assume here as well) and if it works I'll post the skinny.

thanks again.

---

### Post by MysticMetal on 2011-06-30
Good news (to everyone,  or me at least)  I bought a vantec UGT-ST200 ( no I don't work for them) and plugged it in and formatted my drive and put ntfs on it, it all worked fine.  I chose this card because even though it's the same price (roughly) as a much more robust card (raid, more sockets, etc) it was reported to work in linux. it does.  Unfortunately I must have been tired and it is a sata card, not a sata II card but it is working.  So it must have been my bios as inferred by the above helpers.

So thanks a bunch, I can generate a ton of data now.  However there is one thing I haven't fully puzzled out:  I can mount the drive from a terminal but cannot see it in the file browser.  I'll fiddle with it, any suggestions?

---

### Post by psusi on 2011-06-30
STATA-II is backward compatible, so it should work.

---

### Post by alegomaster on 2011-06-30
> **MysticMetal said:**
> Problem:  I'm having difficulties using my brand new 2TB WD SATA II HDD in my old desktop
 When I tried to search for ide drives my bios locked up



The 2 tb drive is not an ide drive.

---

### Post by MysticMetal on 2011-06-30
well after I restarted my computer I was able to mount the 2tb drive with disk utility, and it's good in the file browser now.

Ta-da!  thanks everone, I'm sure to have some issue in the future so we can all hang out again :popcorn:

---

