---
title: "Revert Storage device ID's in Ubuntu 9.10"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by funkyjive on 2009-12-23
Having installed Ubuntu 9.10 on a new machine, the ID's of USB storage devices are represented by the partition ID - i.e. 4 + 4 hex chars. appearing in the /home/media directory.
 
However, attempting to use Ubuntu with pre-compiled duplicator software I require that storage devices are invariably represented in the 'old' incremental naming format, namely /home/media/disk, disk-1, disk-2, etc. In other words, the software scans the /home/media directory for connected devices represented in this format, and does not recognise indeterminate partition ID's.
 
I can also confirm that it is possible to take a device identified in 9.10 in the hex ID format and plug it into another machine with an older Ubuntu installation, and it appears in the desired "disk..." naming format.
 
I would therefore appreciate simple-to-follow instructions (as a newbie) as to how I can force Ubuntu 9.10 to revert to the old identification format for all USB storage devices ordinarily appearing in the /home/media directory.
 
If this is not possible then I am prepared to source and install an earlier version of Ubuntu, so would appreciate knowing which version number is the latest that retains the old naming format.
 
With thanks in advance.
 
FJ

---

### Post by ThaddeusW on 2009-12-23
Not sure if this is a fix but how about you create symbolic links to the devices in the /media directory? 

For example, cd to /media and:
```

sudo ln -s 4f5a-6c9d disk1

```

This would make a link to the 4f5a-6c9d directory called disk1. So if you cd to /media/disk1 its the same thing as 
cd /media/4f5a-6c9d.

That should solve your problem but you have to manually mount and link them.

---

### Post by funkyjive on 2009-12-23
Many thanks for your reply and suggestion.
 
The problem I face is that the software is for duplication purposes, so the actual partition ID's of the connected devices is always changing. Therefore, mapping partion ID's to the old naming convention would require manually re-mapping around a hundred fresh flash devices for each duplication run :(
 
I have successfully used your suggestion for mapping a LAN-shared location (AKA 'address') to a directory so that I have a virtual directory to point the program at for accessing source files to be duplicated, though this was possible as the address remains unchanged.
 
I can understand the reasons why this *apparent* change was implemented, but is sadly impossible to work with if I'm unable to revert to 'relative' device associations using the old incremental naming convention.
 
Hopefully reverting back to the old 'Disk...' naming convention is somehow provided for in the latest Ubuntu 9.10 release, as Linux resolves the issue with Windows drive letter limitations (i.e. 26 unique devices max) for USB flash duplication applications. If not, the only alternative would be to revert to an older version of Ubuntu, once I've established the appropriate release version.
 
Nonetheless, thank you again for your time to reply :)
 
 
FJ

---

### Post by funkyjive on 2010-01-09
Having formerly installed Ubuntu 8.04 Hardy Heron, realising a fast smooth system and facing no issues with drive identification or system stability, and then seeing the system reduced to a crawl with the latest release when enumerating fresh devices for duplication, I have decided to revert to 8.04 for the foreseeable future. The latest 9.10 appears to struggle with 98 flash devices connected, whereas 8.04 walks it with ease.

I believe that there have been considerable changes in the kernel that result in changes in behaviour and different manner of enumerated drive representation, reinforced by the absence of a suitable workaround to revert back to the "Old" representation (i.e. "/media/Disk-x" for enumerated drives).

So, with the favourable 8.04 and the potential for updates that will potentially screw  my system and software again, if I should update 8.04 will this potentially impact the characteristics of the operating system in ways that will put me back to the situation I currently find myself in?

If this is just driver updates then fair do's.

Thanks in advance,

FJ

---

### Post by Methuselah on 2010-01-09
It should be possible to create udev rules to automatically create symlinks with a different naming convention.
But it seems that the real solution is for a new version of whatever software you're using that can cope with the modern kernel.
Sticking with 8.04 which is LTS and still supported might be the best workaround for now.

---

