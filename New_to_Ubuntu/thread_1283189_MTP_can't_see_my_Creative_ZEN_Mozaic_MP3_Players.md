---
title: "MTP can't see my Creative ZEN Mozaic MP3 Players"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by tylersontag on 2009-10-05
I got a new MP3 player a while back, upgraded (or rather replaced) from an older Creative zen model.  Now i had used Gnomad to connect to my old device but its not working on this new one (a Creative ZEN Mozaic)

THe device mounts and i can drop songs strait into the Music folder, the only problem is i can't make playlists this way.

THe error i get is "No jukeboxes found on USB bus"  I've tried another MTP manager (kzenexplorer) with no luck.  I installed mtp-tools and none of the mtp commands can see my device.

I've tried to run these programs as sudo and i've tried unmounting the device while its connected and running the programs but nothings working.  

Any ideas?

---

### Post by wildman4god on 2009-10-05
You'll need to run two commands, first unplug your mp3 player then run "sudo lsusb" note the last few lines, then plug in the mp3 player and run the command again and note which lines get added to the end of the command output. post both results here.
 
Do the same thing with "sudo dmesg | tail"

---

### Post by tylersontag on 2009-10-05
lsusb:
Bus 002 Device 008: ID 041e:201c Creative Technology, Ltd 


then for the other one:

**tag@dell-desktop:~$ sudo dmesg | tail**
[1027446.580831] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[1027446.582879] sd 10:0:0:0: [sdd] 960128 4096-byte hardware sectors: (3.93 GB/3.66 GiB)
[1027446.583757] sd 10:0:0:0: [sdd] Write Protect is off
[1027446.583761] sd 10:0:0:0: [sdd] Mode Sense: 3e 00 00 00
[1027446.583764] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[1027446.583771]  sdd: sdd1
[1027446.597548] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[1027446.597666] sd 10:0:0:0: Attached scsi generic sg4 type 0
[1027624.358817] usb 2-4: USB disconnect, address 8
[1027624.390395] scsi 10:0:0:0: rejecting I/O to dead device
**tag@dell-desktop:~$ sudo dmesg | tail**
[1027687.447040] sd 11:0:0:0: [sdd] Write Protect is off
[1027687.447043] sd 11:0:0:0: [sdd] Mode Sense: 3e 00 00 00
[1027687.447046] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[1027687.448443] sd 11:0:0:0: [sdd] 960128 4096-byte hardware sectors: (3.93 GB/3.66 GiB)
[1027687.448902] sd 11:0:0:0: [sdd] Write Protect is off
[1027687.448905] sd 11:0:0:0: [sdd] Mode Sense: 3e 00 00 00
[1027687.448908] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[1027687.448912]  sdd: sdd1
[1027687.462614] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[1027687.462692] sd 11:0:0:0: Attached scsi generic sg4 type 0

---

### Post by tylersontag on 2009-10-06
bump? it seems like i just need to configure/install something here, since i'm seeing the device, just a certain service can't see it...

---

### Post by DarinB on 2010-03-19
how about with a samsung sch u450

---

### Post by rjs1064 on 2010-04-06
i had problems with samsung haven't found a fix except to use it in drag and drop, disable mtp in the system menu on the player. it keeps dropping in and out and won't chatge.

---

