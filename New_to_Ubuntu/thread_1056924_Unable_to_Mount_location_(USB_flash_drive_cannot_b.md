---
title: "Unable to Mount location (USB flash drive cannot be mounted)"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by khfrekek on 2009-02-01
When I plug in any of my usb flash drives, nothing happens.  If I go to places>Computer, it shows up as USB Drive.  If I try to double click it it says "Unable to Mount location."  Any ides on how to mount this?
Oh and I'm using Hardy Heron.
Thanks,
Zack

---

### Post by XanTrax on 2009-02-01
> **khfrekek said:**
> When I plug in any of my usb flash drives, nothing happens.  If I go to places>Computer, it shows up as USB Drive.  If I try to double click it it says "Unable to Mount location."  Any ides on how to mount this?
Oh and I'm using Hardy Heron.
Thanks,
Zack

There should be a little arrow that you can expand for more error information.  What happens when you try this?

Each line is a single line of command

```

sudo mkdir /media/usb
sudo mount -t TYPE /dev/sdb1 /media/usb/

```

where TYPE is the type of: ext3, fat, fat32, ntfs, etc.  If it is ntfs, try using

```

sudo mount.ntfs-3g /dev/sdb1 /media/usb

```

Post the output and/or the error message from when it says "unable to mount location".

---

### Post by khfrekek on 2009-02-01
Under where it says unable to mount location all it says is "can't mount file," no list arrows.

when I entered sudo mkdir /media/usb, the output was:
mkdir: cannot create directory `/media/usb': File exists

when I entered sudo mount -t FAT32 /dev/sdb1 /media/usb/, the output was:
mount: special device /dev/sdbl does not exist

:(

---

### Post by XanTrax on 2009-02-01
> **khfrekek said:**
> Under where it says unable to mount location all it says is "can't mount file," no list arrows.

when I entered sudo mkdir /media/usb, the output was:
mkdir: cannot create directory `/media/usb': File exists

when I entered sudo mount -t FAT32 /dev/sdb1 /media/usb/, the output was:
mount: special device /dev/sdbl does not exist

:(

Ok, please post the output of

```

ls -al /media
sudo fdisk -l

```

---

### Post by khfrekek on 2009-02-01
Oh nevermind, I fixed it! I plugged it into our Windows computer, the computer found it just fine, so i copied a few files into it, and now it is detected on my linux computer.  very strange.. Thanks so much for all your help though! :D

---

### Post by XanTrax on 2009-02-01
> **khfrekek said:**
> Oh nevermind, I fixed it! I plugged it into our Windows computer, the computer found it just fine, so i copied a few files into it, and now it is detected on my linux computer.  very strange.. Thanks so much for all your help though! :D

Probably just had to be unmounted properly.  I am still interested as to why it didnt find it as /dev/sdb1, all well.

---

### Post by dave r on 2009-02-01
I found this thread most interesting. I have an external hard drive, 160gb Freecom. I mounted it during installation and it has worked fine. I use it mostly for backups and as a location for some big folders. Yesterday while plugging in an USB extension lead, I needed the bluetooth dongle moved of the back of the computer, I plugged it into a different USB socket. I then coulden't get access to it and in the end I rebooted into windows to check it was still working, it was, I had restarted the computer while trying to work out what had gone wrong, but back into Ubuntu without resolving it.   When I came back to Ubuntu there it was working normally. If anyone knows what this was I would like to know just in case it happens again.

---

### Post by Hobgoblin on 2009-02-01
> **XanTrax said:**
> Probably just had to be unmounted properly.  I am still interested as to why it didnt find it as /dev/sdb1, all well.

Might have been a typo?

> when I entered sudo mount -t FAT32 /dev/sdb1 /media/usb/, the output was:
mount: special device /dev/sdbl does not exist

---

### Post by XanTrax on 2009-02-01
> **Hobgoblin said:**
> Might have been a typo?

Ah ya, I see it now.


> **dave r said:**
> I found this thread most interesting. I have an external hard drive, 160gb Freecom. I mounted it during installation and it has worked fine. I use it mostly for backups and as a location for some big folders. Yesterday while plugging in an USB extension lead, I needed the bluetooth dongle moved of the back of the computer, I plugged it into a different USB socket. I then coulden't get access to it and in the end I rebooted into windows to check it was still working, it was, I had restarted the computer while trying to work out what had gone wrong, but back into Ubuntu without resolving it.   When I came back to Ubuntu there it was working normally. If anyone knows what this was I would like to know just in case it happens again.

Well, I cant really explain that.  What I can explain is sometimes when USB hardware is used in both Windows and Linux, sometimes Windows does not release it properly.  I know, for me at least, that sometimes even a regular shut down on my Windows side, my USB jump drive sometimes will not mount and say because of an unclean unmount or unclean device removal on Windows.  Simply forcing the mount, rebooting the machine, and/or just logging out and logging back in has solved some very quirky USB hardware problems for me. Primarily because sometimes the USB hardware needs some kind of reset to reinitialize it.

---

### Post by dave r on 2009-02-01
XanTrax I know its weird, I was thinking that with it working properly from the start I woulden't have to worry about it, obviously not. The thing is the computer is a family one used by everyone and sometimes the drive gets turned of, sometimes the computer won't start with the drive turned on, I think sometimes the computer tries to boot from it, so it would have been nice to find out why it happened and perhaps come up with a way to stop it happening again. At least it wont take me by suprise if it happens again.

---

### Post by XanTrax on 2009-02-01
> **dave r said:**
> XanTrax I know its weird, I was thinking that with it working properly from the start I woulden't have to worry about it, obviously not. The thing is the computer is a family one used by everyone and sometimes the drive gets turned of, sometimes the computer won't start with the drive turned on, I think sometimes the computer tries to boot from it, so it would have been nice to find out why it happened and perhaps come up with a way to stop it happening again. At least it wont take me by suprise if it happens again.

It might be set as a bootable device to try to boot from before the primary HDD.  Try disabling it in the bios.

---

### Post by lean-mini on 2009-03-30
> **XanTrax said:**
> There should be a little arrow that you can expand for more error information.  What happens when you try this?

Each line is a single line of command

```

sudo mkdir /media/usb
sudo mount -t TYPE /dev/sdb1 /media/usb/

```

where TYPE is the type of: ext3, fat, fat32, ntfs, etc.  If it is ntfs, try using

```

sudo mount.ntfs-3g /dev/sdb1 /media/usb

```


lean@lean-minihp:~$ sudo mkdir /media/usb
[sudo] password for lean: 
lean@lean-minihp:~$ sudo mkdir /media/usb
mkdir: no se puede crear el directorio «/media/usb»: El fichero ya existe
lean@lean-minihp:~$ sudo mkdir -t fat32 /dev/sdb1 /media/usb
mkdir: opción inválida -- t
Pruebe `mkdir --help' para más información.
lean@lean-minihp:~$ sudo mount.fat32 /dev/sdb1 /media/usb
sudo: mount.fat32: command not found
lean@lean-minihp:~$ sudo mount.fat /dev/sdb1 /media/usb
sudo: mount.fat: command not found
lean@lean-minihp:~$ sudo mkdir /media/usb
mkdir: no se puede crear el directorio «/media/usb»: El fichero ya existe
lean@lean-minihp:~$ sudo mount -t fat /dev/sdb1 /media/usb
mount: tipo de sistema de ficheros 'fat' desconocido
lean@lean-minihp:~$ sudo mount.fat-3g /dev/sdb1 /media/usb
sudo: mount.fat-3g: command not found
lean@lean-minihp:~$ sudo mount.fat /dev/sdb1 /media/usb
sudo: mount.fat: command not found
lean@lean-minihp:~$ 
Thanks 
lean

---

