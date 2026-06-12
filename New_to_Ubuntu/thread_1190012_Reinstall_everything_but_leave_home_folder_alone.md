---
title: "Reinstall everything but leave home folder alone?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by crazyfuturamanoob on 2009-06-17
I want separate partitions for /home, /grub and stuff, and keep my current home content.

At the moment, they are all on the same partition. I'm too lazy to google.

---

### Post by halitech on 2009-06-17
see here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Dragonbite on 2009-06-17
Well, you'll probably still have to google some.

One option is to copy your /home directory onto a USB drive, then do a fresh install making a seperate partition for your /home directory and copy back your files.

Or re-partition beforehand to make the /home directory (whether or not the system sees and mounts it as the /home directory) and copy your files into the new parititon. ** WARNING: backup your files because if this gets screwed up you could potentially loose your ENTIRE system and not be able to get these files back (YMMV). **

As for /boot (grub).. that is best done during an installation.

If you are looking to do this and not re-install, then you're going to have to do much more than just google ;)

---

### Post by crazyfuturamanoob on 2009-06-17
I got two 320 GB hard disks.

Is it possible to stretch home partition over them both?

---

### Post by Dragonbite on 2009-06-17
> **crazyfuturamanoob said:**
> I got two 320 GB hard disks.

Is it possible to stretch home partition over them both?

I think that is something that RAID may be able to do, but I don't know anything about RAIDs.

You could, though, mount the drive as a folder in your home directory (or mount it under /mnt and create a link to it in your /home directory).

---

