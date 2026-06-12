---
title: "External USB Drive mounts, then immediately unmounts"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Oswulf on 2010-07-08
I've got an external USB drive which for a few months now has automatically mounted when the machine starts.

Now, however, the device appears to mount (a Nautilus window pops up, and about 1 in 10 times this actually lists the files and directories on the device).  However, the Nautilus window almost immediately closes.  This cycle repeats every few seconds.

fdisk -l does not find the device.

I'm thinking this is a software problem, rather than a hardware one because the device works OK attached to another computer.

Any thoughts on what the problem might be?

Thanks.

---

### Post by aeiah on 2010-07-08
see what errors are being logged when you plug it in. run ```
dmesg
```

or if you want to see the errors as they come along, do ```
tail -f /var/log/messages
```
then plug your drive in

---

### Post by Oswulf on 2010-07-08
I'm now getting a new error message:

Unable to mount 1.0 TB Filesystem
Error mounting:mount: /def/sdf1: can't read superblock

That sounds to me like a filesystem corruption.

fsck doesn't work (similar superblock error message).

I'm guessing I need to boot from a CD (to ensure the device isn't mounted), then

sudo e2fsck -b 32768 /dev/sdf1

Does that sound right?

If you still think the dmesg output will be helpful, please let me know.

Thanks again.

---

### Post by Todamont on 2012-05-28
Ok, I had this problem. I realized it could be fixed by unplugging my cellphone while the USB drive is attached. Seriously, it worked. Take a look at this bug in ehci_hcd module... unfixed yet. Cheers~

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746)

[edit] ok strangely this bug is marked as "won't fix", I've never seen that before...

---

