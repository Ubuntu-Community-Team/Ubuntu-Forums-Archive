---
title: "problem mounting external harddisk, dropped on the floor"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by enetic on 2010-10-01
Im having some problems mounting my maxtor external harddisk. I accidentally unplugged the usb connector when i was watching a movieclip, and then i also dropped it on the floor.. I wouldnt say it were a severe hit, but i dont know if it could be the reason why i cant mount it?

---

### Post by johnharris on 2010-10-01
> **enetic said:**
> Im having some problems mounting my maxtor external harddisk. I accidentally unplugged the usb connector when i was watching a movieclip, and then i also dropped it on the floor.. I wouldnt say it were a severe hit, but i dont know if it could be the reason why i cant mount it?

yeah prolly, you can try to plug it in and run lsusb in terminal and see if it shows up at all.

---

### Post by coffeecat on 2010-10-01
We need to see whether there's physical damage sufficient to prevent the drive being detected, and/or whether there's filesystem corruption from the unclean unmount.

Plug the drive in and switch it on. Then post the output of these two terminal commands:

```
dmesg | tail
sudo fdisk -lu
```

**Edit:** should have added. That's only for starters. If it shows up in fdisk we can then investigate to see if there's filesystem corruption.

---

### Post by enetic on 2010-10-01
thats bad.. because my first try was the lsusb, and it doesnt show up there :(.. 

so i guess its broken then? or?

thanks for the help anyways!

---

### Post by coffeecat on 2010-10-01
Failure to show up in lsusb is certainly discouraging, but it would be sensible to confirm this with the output of 'dmesg | tail'.

Before you write it off, open up the case and see if any cables have been dislodged inside. And do you have another USB enclosure you could try it in? The drive itself may or may not be damaged. The problem might be with the circuitry in the enclosure.

Also - is this a 3.5" drive with a separate power supply? Did you drop the power supply on the floor? These types of power supplies are prone to failure, so there are several things to check out. If the drive is still good but either the enclosure or the power supply have failed, you would still have a hard drive you might be able to use inside the computer case.

---

### Post by enetic on 2010-10-02
here's the response i got for dmesg | tail:

paal@paal:~$ dmesg | tail
[   21.152624] CPU0 attaching sched-domain:
[   21.152630]  domain 0: span 0-1 level MC
[   21.152634]   groups: 0 1
[   21.152642] CPU1 attaching sched-domain:
[   21.152645]  domain 0: span 0-1 level MC
[   21.152648]   groups: 1 0
[   27.140030] eth0: no IPv6 routers present
[  175.033193] eth0: link down.
[28142.926157] eth0: link up.
[28194.904997] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
paal@paal:~$

---

### Post by coffeecat on 2010-10-02
> **enetic said:**
> here's the response i got for dmesg | tail:

No sign of the external drive being detected I'm afraid. Bad news but at least it confirms lsusb.

The only other thing I can suggest is to test the different bits of hardware as I described earlier. I hate to throw out any hardware that might be re-cyclable. You may have a perfectly good HD in a broken enclosure. Or a broken HD in a re-usable enclosure. The cost of a replacement bare HD or replacement enclosure will be less than a brand-name external USB drive. Or it may be as simple as a loose connection inside. Or as bad as everything broken. Worth investigating.

---

### Post by enetic on 2010-10-02
yea... i tried mounting it in the computer, but i guess i didnt have extra space for hdd's. are there any other ways of doing this? or is it possible to buy a new SATA cable and try that way? because i just used the power and sata cable from the cdrom?

i really appriciate your help!

thanks

---

### Post by coffeecat on 2010-10-02
> **enetic said:**
>  or is it possible to buy a new SATA cable and try that way? because i just used the power and sata cable from the cdrom?

A SATA  optical drive uses the same power and data cables as a hard drive, so if you tried the bare Maxtor drive with the optical drive's cables and it wasn't detected then the drive is almost certainly a goner.

Sorry.

---

