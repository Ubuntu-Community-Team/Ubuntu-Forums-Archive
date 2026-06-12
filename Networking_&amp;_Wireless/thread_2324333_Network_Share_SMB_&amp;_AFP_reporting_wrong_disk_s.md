---
title: "Network Share SMB &amp; AFP reporting wrong disk size"
date: 2016-05-12
forum: Networking &amp; Wireless
---

### Post by Greg_OBrien on 2016-05-12
Hello All,
I'm looking for some incite on a strange issue I'm having with a hardware raid array.
Currently I took an old HP DL380 G5 with an HP P800 hardware raid controller and connected it to an MSA60 12-bay array.

Hardware wise everything is working fine, I put the drives into a raid 6 configuration and the system reported 9.2TB useable. Installed ubuntu server, downloaded samba and netatalk,
setup their configurations, and tested the ability to write in both AFP & SMB modes.  This part is just about working fine except I'm getting an error on the drive capacity.

When i use df -h on my terminal it returns the array at 9.1TB in Size (again in line with what the hardware raid told me)
[SIZE=7][ATTACH=CONFIG]269015[/ATTACH][/SIZE]
however when I SMB or AFP into the share (through my Mac laptop) I get 9.82TB in Size...
[ATTACH=CONFIG]269016[/ATTACH]

I know it's reporting the right drive, but I'm not sure where the extra 810gb are coming from or how to fix it?
Before reaching out on the forum I tried tune2fs which affects both df & the network share equally so this doesn't seem to help.  The only thing I can think of is that the primary OS, which is in another Array off the same raid card, thats is around 800gb, perhaps that's being added to the total?  Is there a way to alter what get's reported to the computers using the share?

Any advice would be greatly appreciated!

---

