---
title: "mounting a usb drive"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by brijraj22 on 2009-03-09
how can i mount an external usb drive if the ntfs is still marked to be in use?
i used it on windows vista and despite several attempts, could not remove it safely, so i just pulled out the usb plug.now when i used it on another comp running ubuntu 8.04, i cannot open it with the error message that ntfs is in use. can someone help me?

---

### Post by drs305 on 2009-03-09
You can either try to 'force' mount the device or try ntfsfix, part of the ntfsprogs app that you can download via synaptic. (Refer to the *man* page for the command options for ntfsfix).

For the mount command, you can use the following. Substitute you device for "dev/sda1" and the correct mount point for "/media/windows":
```

sudo mount -t ntfs-3g -o force /dev/[COLOR="DarkRed"]sda1[/COLOR] [COLOR="DarkRed"]/media/windows [/COLOR]

```

---

### Post by albandy on 2009-03-09
paste the full error here please, I need it to send you the correct mount line, it will be somethig like this:

sudo mount /dev/sdc1 /media/disk -o force
or could be
sudo mount /dev/sdd1 /media/disk -o force
....
depending on the number of hard disk and usb devices installed on your system

---

### Post by kanikilu on 2009-03-09
```
sudo mount -t ntfs-3g /dev/sdb1 /media/usb -o force
```

Notes:

- replace /dev/sdb1 with the name for your device, it should tell you in the error message, or you can use "dmesg | tail" to find out.

- replace /media/usb with a mountpoint that exists, so if necessary use "sudo mkdir" to create a directory to use as the mountpoint

// Edit - Too slow ;)

---

### Post by brijraj22 on 2009-03-09
thank you all :), the problem has been solved

---

