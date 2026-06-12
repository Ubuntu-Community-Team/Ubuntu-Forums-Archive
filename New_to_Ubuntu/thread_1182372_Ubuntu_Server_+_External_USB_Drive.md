---
title: "Ubuntu Server + External USB Drive?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by kevmev12 on 2009-06-08
Hi all. I'm running a headless Ubuntu Server 9.04 with samba as a file server, and I need to transfer a few hundred gigs of data from the server to an external USB drive. I've been copying files by connecting the USB drive to a laptop, and copying it over via the network, but found that it's too slow. I'd like to connect the USB drive directly to the server and perform the file transfer without using the laptop or my home network as the middle-man for the transfer (except of course to control the server via PuTTY). The external USB drive is a FAT32 so there shouldn't be any problems recognising the drive. From my research, I've found that I'm meant to manually mount the USB drive to the server, but it seems different websites have different solutions.

How do I go about mounting a USB external drive to the server and to copy the files across from the server to the drive?

---

### Post by 123456789123456789123456 on 2009-06-08
As far as I know, regardless of rather it is server or desktop edition, Ubuntu should reconize the disk, and automatically mount the drive
if for some reason it does not mount, you can mount the drive, by either going to places, and selecting the drive to mount it, or mount it from the terminal, using mount command, should be under /dev, can't remember exact folder, possible /etc/dev/ not sure but may even be listed as usb1.
copying can and probably be controled by the file manager installed on the system.  Drag and drop is the most common method.

---

### Post by dileepm on 2009-06-09
```
sudo gedit /etc/hal/fdi/policy/preferences.fdi
```

Replace all false to true and reboot your system you may hot plug your USB no mounting commands.

---

