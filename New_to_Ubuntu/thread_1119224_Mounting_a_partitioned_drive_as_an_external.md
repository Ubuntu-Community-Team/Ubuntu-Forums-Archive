---
title: "Mounting a partitioned drive as an external"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Dj Dutchman on 2009-04-07
Hi, my current HDD in my laptop has 3 partitions (1 for Ubuntu, 1 for Ubuntu Studio and another for XP). Now I'm getting an a new HDD to replace the current one but I don't want to specifically back everything up. Would it be possible to pop my current HDD in an external and then mount it so I can copy stuff over as I see fit? Would the partitioning mess everything up? Cuz in reality, the stuff I wanna keep is all on the plain Ubuntu install, so if it made my life easier I could delete the other two partitions...

Lemme know what's the best way to do this

Thanks

---

### Post by Hospadar on 2009-04-07
It's quite possible, although it may depend on what kind of hdd you have.

Most not too new lappies have mini-ide drives in them, which are basically the same as an ide drive just with a slightly sqeezed together set of pins.  You can get adapters to regular ide real cheap.  Newer drives are probably some kind of mini-sata or something, I assume similarly cheap adapters exist.  So assuming you have or you acquire an external enclosure, yes, you should be able to connect and use it just fine.

Depending on how the enclosure works and maybe what partitions exactly are set up, ubuntu may not auto-mount your partitions, but it's no biggie to just mount them by hand to get whatever you need

If you do "sudo fdisk -l" it will show you all the connected devices, then you can take the device name fdisk gives you (something like /dev/sdb1 or whatev) and do a mount:
"sudo mount -t ext3 <device name>"
or
"sudo mount -t ntfs-3g <device name>" (this one might just be ntfs, not ntfs-3g, just try em both) for your windows part

---

### Post by Dj Dutchman on 2009-04-08
Thanks. Ya, I know all about the HDD side of things, I just wasn't sure bout the mounting side of things...

---

