---
title: "Several Ubuntu 9.10 installed"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by murkydismal on 2009-11-16
[FONT=Arial Black][SIZE=2]First and foremost, I’d like to thank everyone that has participated in the global construction project that is Ubuntu. Kind of gives one hope for the world! I’ll be finally free from windows, free at last![/SIZE][/FONT]
 
[SIZE=2][FONT=Arial Black]My intention:[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]I installed Ubuntu 9.10 automatically on a partition Ubuntu made. I had 4 partitions: Recovery (emachines), Windows XP, Ubuntu 9.10, 1.1 Ubuntu swap disk. Install went perfect, everything worked as far as I could tell. I liked Ubuntu and decided to reinstall using the greatest portion of my disk.[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]During reinstall I had a little trouble dealing with partition choices. I tried it several times, at one time having grub problem which appears to be fixed. I could not find a way to just format the 146 GB portion to do a clean install for just Ubuntu 9.10. This is what I did end up with:[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]160 Hard Disk-ATA st3160021a-MBR partition table[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-8.6 GB file system-NTFS, Windows XP[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-Recovery-5.2 GB FAT 32-bit version[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-146 GB Extended-contains logical partitions[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-1.1 GB swap file[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-71 GB file system-Linux Ext 4 (version 1)[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-1.1 GB swap space[/FONT][/SIZE]
[SIZE=2][FONT=Arial Black]-73 GB free unallocated space[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]The 71 GB and the 73 GB appear to both have a full set of Ubuntu files. When I try to use help and follow instruction, for example:[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]Synaptic Package Manager search for ndiswrapper-utils, it cannot be found. Same with other packages? that need to be installed and found. At one point, I searched the other (not in use?) partition and it was found, but I couldn’t install?/use or just don‘t know how?[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]I’m not sure exactly what’s going on having no experience with Ubuntu, do I have several Ubuntu 9.10’s installed? Can I do one clean install on the 146GB portion? How?[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]Lastly, it should be noted that while I own at least 4 Windows XP, I do not have the disk for reinstall for this particular computer, so for the time being, I’d rather not lose it. Since I cannot replace it without spending hundreds. That was the final nail in the coffin for windows, for me![/FONT][/SIZE]
 
[SIZE=2][FONT=Arial Black]Thanks, murkydismal[/FONT][/SIZE]
[FONT=Arial Black][SIZE=2][/SIZE][/FONT] 
[FONT=Arial Black][SIZE=2]Note:  I could not use tab or manual indent or it would be easier to understand.  Please note: that the 146 GB disk contains all the partitions listed below it.[/SIZE][/FONT]

---

### Post by slakkie on 2009-11-16
Could you reformat your post. It is a pain to read. Until then, goodbye.

---

### Post by murkydismal on 2009-11-16
Thank you slakkie for the reformat comment I feel the same way, as I said at the bottom.  This is the first time I've posted on this forum and I could not figure out how to indent paragraphs or use tab.  I did it manually, copied paste, tried tabs, etc.  Perhaps, you could help?

---

### Post by oldos2er on 2009-11-16
Both ndiswrapper-common and ndiswrapper-utils-1.9 are in the main repository. Run ```
sudo apt-get update && sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
``` and see if that works for you. If not, please post any errors here.

Regarding your partitions, can you post the output of this command? ```
sudo fdisk -l
```

---

