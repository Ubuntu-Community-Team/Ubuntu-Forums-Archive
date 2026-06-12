---
title: "Can no longer see external hard drive"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by hybrid180 on 2010-03-24
Hi,

I am new to Ubuntu and have Ubuntu 9.10 installed.  I recently bought a Seagate 2TB external hard drive.  I connected it via usb and was working just fine when I first connected it.  Then I unmounted it and reformated in ext4 format.

After the format I was able to mount it and was still working fine, meaning I could access the drive no problem.

I have since rebooted my machine and now it takes about 3 minutes to boot when before it was more like 30 seconds.  I can also no longer see the drive either.  Is there something I should do so I can see the drive again?

When I do: ```
sudo fdisk -l
```

I do not see the drive listed, all I see are /dev/sda drives.  When before the reboot I would see /dev/sdb.

Any help would be appreciated.

Thanks

---

### Post by Ozymandias_117 on 2010-03-24
Does it show up as a USB device in ```
sudo lsusb
```

---

### Post by hybrid180 on 2010-03-24
lsusb took a really long time and when it finally came back it wasn't listed.

However, I moved the drive to my windows machine and plugged it in there.  Of course windows did not recognize it since it was using the ext4 file system.  But when I moved it back to my linux machine it recognized it once I plugged it in.

I think maybe cause I had to unplug the external power supply to the external hard drive to move it?  

But anyways, all is well now, thank you for your help Ozymandias_117

---

