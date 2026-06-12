---
title: "[SOLVED] Mounting an NTFS volume"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by cyclone5uk on 2008-12-18
Just a quick question:

When you mount an NTFS drive using the GUI (not in terminal) is it read-only by default?

If not can I set it so that it is read-only?

---

### Post by HotShotDJ on 2008-12-18
The easy, GUI way:

1) Install ntfs-config (either through Applications --> Add/Remove Applications or System --> Administration --> Synaptic Package Manager)

2) Once installed, run Applications --> System Tools --> NTFS Configuration Tool.  Enable Write support as appropriate for your system.

---

### Post by cyclone5uk on 2008-12-18
Thanks!

---

### Post by lernatix on 2008-12-20
I just tried NTFS-config.

Trying to get my windows drive writable.

I get this error.

```
Mounting /media/sda1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g force 0 0
```

Not sure what i'm doing wrong, just want to copy files from 
Ubuntu (Hardy) to my windows drive.

---

### Post by BDNiner on 2008-12-20
That occurs when the NTFS file system is not closed properly by windows. Windows does not care about this but Linux does. You will have to connect the drive back to a windows computer and use the safely remove hardware option or eject it from My Computer, or mount it using the force command in the error message.

---

### Post by lernatix on 2008-12-20
Its an internal drive!!!

So i guess i'll have to force it?

The damn thing was mounted (read only)
untill I tried to gain write permission 
with NTFS config.

EDIT: OK all good. 

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

Thanks BDNiner

---

### Post by tomtom1982 on 2008-12-20
To copy files from ubuntu to windows you can do this from your windows installation. All you have to do is to install the ext3-driver in windows. You´ll find it here:

[HTML]http://www.fs-driver.org/download.html[/HTML]

---

