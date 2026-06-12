---
title: "Installing external harddrive"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by dtommy79 on 2009-01-14
Hi,

I cannot use my extarnal hard drive, I get this error message:

> Cannot mount volume.
Unable to mount the volume.

In the description it says:

[IMG]http://kepfeltoltes.hu/090114/hardware_www.kepfeltoltes.hu_.gif[/IMG]



I also get this message:

> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Michael.Godawski on 2009-01-14
hi,

if you have windows installed somewhere then plug the external drive into windows and safely remove it. Then switch back to Ubuntu and try again.

Also please post the results of these terminal commands while the drive is plugged in:

```
sudo fdisk -l
cat /etc/fstab
mount
df -h
```

---

### Post by Paqman on 2009-01-14
What's happened is that your drive hasn't been unmounted properly last time you shut down. To prevent this happening make sure you unmount any external drives before shutting down the OS.

If you have Windows installed just boot up, unmount the drive manually, then reboot into Ubuntu. If you don't have Windows you'll have to use the mount command given in that (heinous) error message.

---

### Post by northern lights on 2009-01-14
Your external drive appears to be formatted as ntfs.

ntfs filesystems carry a marker on the first few bits. The last time used this drive was most likely via a Windows OS that either crashed or you removed the drive from the USB port without using the Windows native "Safely remove hardware" feature while Windows was running. Hence it did not get cleared.

Either follow the error messages instructions and try to force mount the drive, i.e. open a terminal (Applications > Accessories > Terminal) and run```
mount -t ntfs-3g /dev/sdc1 /media/disk -o force
```or connect it to a machine running windows and do a clean shutdown.

---

### Post by dtommy79 on 2009-01-14
Hi,

Thanks for the answers.

yes, a few files were copied to the hard drive from a different computer that uses windows OS. And now I'd like to copy some files from my computer which runs ubuntu.

So, does it mean that I can only use  this external harddrive with one of the computers?

---

### Post by lswest on 2009-01-14
> **dtommy79 said:**
> Hi,

Thanks for the answers.

yes, a few files were copied to the hard drive from a different computer that uses windows OS. And now I'd like to copy some files from my computer which runs ubuntu.

So, does it mean that I can only use  this external harddrive with one of the computers?

No, not at all, just remember to *safely remove* the external drive before shutting it off (click the safely remove hardware icon in the taskbar in windows and choose the proper drive).  And in Ubuntu always remember to right-click and choose "unmount" before removing the device.  It's something that should be done no matter what, as failure to do so can lead to loss of data.

---

### Post by dtommy79 on 2009-01-14
Thank you, it's working now.

---

### Post by northern lights on 2009-01-14
> **lswest said:**
> No, not at all, just remember to *safely remove* the external drive before shutting it off (click the safely remove hardware icon in the taskbar in windows and choose the proper drive).
+1

> **lswest said:**
> And in Ubuntu always remember to right-click and choose "unmount" before removing the device.  It's something that should be done no matter what, as failure to do so can lead to loss of data.
If the device is mounted with the *async* option (I/O operations are not done simultaneously) this is true. Mounting the device with *sync* (data is written to the drive as soon as file operations are initiated) removal without unmounting should not result in data loss ever.

Conclusively, *async* can be more resource efficient, *sync* safer.

[Related reading]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by lswest on 2009-01-15
> **northern lights said:**
> 
If the device is mounted with the *async* option (I/O operations are not done simultaneously) this is true. Mounting the device with *sync* (data is written to the drive as soon as file operations are initiated) removal without unmounting should not result in data loss ever.

Conclusively, *async* can be more resource efficient, *sync* safer.

[Related reading]("http://www.tuxfiles.org/linuxhelp/fstab.html")

That's true, but it's always easier to get into the good habit of unmounting the drive before removing it, so that in case you end up doing it on a different computer that uses async instead of sync, you don't end up forgetting.  After all, it's not much effort, especially if you add a diskmounter applet.

Thanks for the extra info though.

---

### Post by northern lights on 2009-01-15
> **lswest said:**
> That's true, but it's always easier to get into the good habit of unmounting the drive before removing it
[...]
Thanks for the extra info though.
No doubt. Didn't mean to contradict.

---

### Post by Vinyamar777 on 2009-01-15
May the sun shine on your path.

I've had an ext. hdd left on when I did an OS reinstall (Vista), inaccessible since.  Just the tip of unmounting in Win, then opening in Ubunutu, did the trick.

As Columbus apparently said, it's easy when you know how.:D

---

