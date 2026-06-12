---
title: "Formatted windows drive how to mount?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by rossmwood on 2008-12-20
How do I mount a drive I used to use on windows?  I reformatted it with gparted as an ext/3 filesystem but it isn't mounted.

---

### Post by MyR on 2008-12-20
Have you tried using nautilus? Try in Places > Computer and double click the drive. It should mount and open automatically.
peace

---

### Post by rossmwood on 2008-12-20
I used nautilus but there wasn't an icon for it, bit it comes up in gparted.

---

### Post by candtalan on 2008-12-20
Is the drive now connected into the computer?

Did this ex Windows drive, used to run this computer? If so, be aware that it will still contain the MBR to boot the computer, even after formatting.

The mechanical jumper connection on the drive/s will be relevant. A single drive will be expected to be set as master, and with two drives on the same IDE bus will be:
one master, the other, slave.

If both drives worked ok in th esame pc previously and habve not been physically re arranged, then the master slave setings wil probably be ok.

Is the drive shown when using  the menu item
Places>Computer?

If not then examine the file
/etc/fstab
because an entry here will be needed one way or another.

---

### Post by MyR on 2008-12-20
Can you paste the output of
```
sudo fdisk -l
```

---

### Post by logos34 on 2008-12-20
You need to make a mountpoint, edit permissions and add an entry to fstab (if you want it to automount at startup).  This guide walks you through it:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bodhi.zazen on 2008-12-20
To mount a partition you need to make a mount point and then mount it with the mound command.

For example :

```
sudo mkdir /media/foo
sudo mount /dev/sdxy /media/foo
```

Set ownership and permissions with chown and chmod.

To enable it to automatically mount at boot you need to add an entry in /etc/fstab.

If you like you can use UUID. You can list your partitions by UUID with :

```
sudo blkid
```

See this link :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

