---
title: "Mounting an NTFS partition"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Driventemple on 2009-03-08
Hi,

I'm a new Ubuntu convert (Ithink!)  I have a NTFS partition on the harddisk with all my data I will need to transfer.  I installed 8.10 and when I try to find my data its not where I expected it to be - /media/windows.  Using GParted I can see the partition: dev/sda2.

sudo mount /dev/sda2 /media/disk gives me this message:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/disk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/disk ntfs-3g force 0 0

When try to use mount -t ntfs-3g /dev/sda2 /media/disk -o force

I get the message 'only root can do that'.  I am unable to log on as root either using my own password or none.

Sorry if this is a simple matter that a 'wimp' can't handle, but some help would be appreciated

---

### Post by taurus on 2009-03-08
Are you the original user that you created during the installing process?  When it asks for your password, you won't see any display, not even ***, on the screen when you type in your password so make sure you type the right one and hit Return.

You can fix that problem for your ntfs filesystem with ntfsfix.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
df -h
```

---

### Post by Driventemple on 2009-03-08
Worked perfectly!  Thank you very much:D

---

### Post by mrbiggbrain on 2009-03-08
> **Driventemple said:**
> Worked perfectly!  Thank you very much:D

actualy it works sloppy, its best to release the drive if you can, doing this simply requires a proper shutdown of the windows partition.

---

