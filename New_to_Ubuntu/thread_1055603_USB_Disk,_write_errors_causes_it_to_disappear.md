---
title: "USB Disk, write errors causes it to disappear"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Rich663 on 2009-01-30
I'm pretty new at this but have a little unix experience from years ago, so be low level with me, thanks.
My problem is that when I put my USB drive, a Samsung 160GB drive formated NTFS, it gets weird.
First it will mount just fine. I can open everything on it.
When I try to copy data from my internal drive to it it may take some of it, like the file headers and some of the ASCII files then stop. It disappears from the mount and I can't get it to remount. If I unplug it and plugg it back in, I either get nothing or an error message saying the device is unreadable, has a hardware problem or is in a raid configuration.
If I reboot the PC with the repair option, the only way it will boot, but that is another problem, I can plug the USB drive in and it is recognised.

Any idea why I can only copy real small files to it or why it stops and disappears?

---

### Post by cmnorton on 2009-02-01
You might need to do some searching as to how to write to ntfs formatted disks.

I found this:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Just for some general information, would you describe your hardware and whether the motherboard supports USB 2.0?

Please look in your logs /var/log/syslog and /var/log/messages

right after the disk goes away. 

You can prefix the full log path with sudo tail /var/log/<whatever> and see the last few items logged.

You are looking for anything tell-tale as to what happened during a large write.

---

### Post by Rich663 on 2009-02-01
Great news I hope, It worked this time....

It is an older PC with USB 1.1 according to Ubuntu's Device Manager.
I had already installed the NTFS configuration tool to deal with an internal disk problem. In that case it didn't help and I had to reformat the drive ext3.

When I connected the external drive today, Ubuntu didn't see it at all. I rebooted the system but it failed the reboot, locking up with a network message last thing on the screen.
Power off/on and boot with repair and use recovery mode (the only way this machine will boot and run).
Connect the Samsung USB drive and it is recognized, mounted sdc1, and had no trouble writing complete folders of more than 250 MB.

I give up, it worked, backed up my data drive. 

Now if I can figure out why it will only boot in recovery mode I'll be a lot happier, but that will have to be another thread.

THANKS for your suggestions.
Rich

---

