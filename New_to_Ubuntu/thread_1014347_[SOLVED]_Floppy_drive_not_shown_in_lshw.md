---
title: "[SOLVED] Floppy drive not shown in lshw"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by boof1988 on 2008-12-17
The below operating system is not showing the floppy drive.

The BIOS will give an error if there is a (non-boot) floppy in the drive during boot-up so, I believe, the drive is recognized during boot but not in the operating system.

Xubuntu 8.10
Dell Optiplex GX110
256Mb RAM

sudo fdisk -l

```
Disk /dev/sda: 8447 MB, 8447459328 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9650e4e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          32      257008+  83  Linux
/dev/sda2   *          33         159     1020127+  82  Linux swap / Solaris
/dev/sda3             160         592     3478072+  83  Linux
/dev/sda4             593        1027     3494137+  83  Linux
```

sudo lshw -short

```
H/W path           Device       Class      Description
======================================================
                                system     OptiPlex GX110
/0                              bus        OptiPlex GX110
/0/0                            memory     64KiB BIOS
/0/400                          processor  Pentium III (Coppermine)
/0/400/700                      memory     32KiB L1 cache
/0/400/701                      memory     256KiB L2 cache
/0/1000                         memory     256MiB System Memory
/0/1000/0                       memory     128MiB DIMM SDRAM Synchronous 100 MHz (10.0 ns)
/0/1000/1                       memory     128MiB DIMM SDRAM Synchronous 100 MHz (10.0 ns)
/0/100                          bridge     82810E DC-133 (GMCH) Graphics Memory Controller Hub
/0/100/1                        display    82810E DC-133 (CGC) Chipset Graphics Controller
/0/100/1e                       bridge     82801AA PCI Bridge
/0/100/1e/c        eth0         network    3c905C-TX/TX-M [Tornado]
/0/100/1f                       bridge     82801AA ISA Bridge (LPC)
/0/100/1f.1        scsi0        storage    82801AA IDE Controller
/0/100/1f.1/0      /dev/sda     disk       8447MB ST38421A
/0/100/1f.1/0/1    /dev/sda1    volume     250MiB EXT3 volume
/0/100/1f.1/0/2    /dev/sda2    volume     996MiB Linux swap volume
/0/100/1f.1/0/3    /dev/sda3    volume     3396MiB EXT3 volume
/0/100/1f.1/0/4    /dev/sda4    volume     3412MiB EXT3 volume
/0/100/1f.1/1      /dev/cdrom   disk       DUW1616/ARR
/0/100/1f.1/0.1.0  /dev/cdrom1  disk       SCSI CD-ROM
/0/100/1f.2                     bus        82801AA USB Controller
/0/100/1f.3                     bus        82801AA SMBus Controller
/1                 pan0         network    Ethernet interface
```

---

### Post by handydan918 on 2008-12-17
Have you tried mounting it with a disc inserted? I have a gx110 right here, and lspci shows nothing, (lshw isn't installed ( it's running Lenny) but it mounts OK.

---

### Post by handydan918 on 2008-12-17
Have you tried mounting it with a disc inserted? I have a gx110 right here, and lspci shows nothing, (lshw isn't installed ( it's running Lenny) but it mounts OK.

---

### Post by boof1988 on 2008-12-17
> **handydan918 said:**
> Have you tried mounting it with a disc inserted? I have a gx110 right here, and lspci shows nothing, (lshw isn't installed ( it's running Lenny) but it mounts OK.

Thanks for the reply.

The drive still didn't show up when I had a disk inserted.  But... I searched the forums again and found the following thread which was helpful.

[http://ubuntuforums.org/showthread.php?t=1011210#2](http://ubuntuforums.org/showthread.php?t=1011210#2)

I tried:

```
sudo mount /dev/fd0 /mount_directory_path
```

and it didn't work until I used:

```
sudo modprobe floppy
```

as indicated in the thread listed above.

I haven't tried to read or write any of the files yet.  And I'd like to know what the "sudo modprobe floppy" does (and why it worked) so I wont mark the thread solved yet.

Thanks again for the response.:p

---

### Post by Rhubarb on 2008-12-17
Intrepid's floppy disk support is different to that of Hardy.
Intrepid's kernel has no support for floppy disks.
To get floppy disks to be recognised, a kernel module (floppy) needs to be loaded.

So as you have found out running "sudo modprobe floppy" does the trick.

Rather than having to run the above command everytime you power on your computer, it would be far better in your case to make the floppy module to load upon startup:

```
gksu gedit /etc/modules
```
Append this to the end of the file in gedit:
```
floppy
```
Then save and exit.

You may now restart your computer.
You'll find that you can access your floppy drives now as usual.
Places --> Computer --> Double click on the floppy drive, and it will be mounted for you.

---

### Post by boof1988 on 2008-12-18
> **Rhubarb said:**
> Intrepid's floppy disk support is different to that of Hardy.
Intrepid's kernel has no support for floppy disks.
To get floppy disks to be recognised, a kernel module (floppy) needs to be loaded.

So as you have found out running "sudo modprobe floppy" does the trick.

Rather than having to run the above command everytime you power on your computer, it would be far better in your case to make the floppy module to load upon startup:

```
gksu gedit /etc/modules
```
Append this to the end of the file in gedit:
```
floppy
```
Then save and exit.

You may now restart your computer.
You'll find that you can access your floppy drives now as usual.
Places --> Computer --> Double click on the floppy drive, and it will be mounted for you.

Thanks for the explanation.  I added a line "floppy" to /etc/modules and there is a floppy icon on my desktop on startup.

The last time I used floppies was about 8 or so years ago and that was in Windoze.  This is my first linux machine to have a floppy drive so I wanted to make a Super GrUB Floppy in case I needed it.  And to use on any other computers which have a floppy drive.

I'm still a little confused on when it is safe to remove the floppy.  Something I'll have to research a bit more.

Thanks again.

---

### Post by handydan918 on 2008-12-18
> **boof1988 said:**
> 

I'm still a little confused on when it is safe to remove the floppy.  Something I'll have to research a bit more.

 Waiting a few seconds after issuing the umount command is usually sufficient to allow any writes to finish.

---

### Post by boof1988 on 2008-12-19
What I have learned:

The floppy drive doesn't have to show up in lshw for it to be mountable.

How to add the floppy drive ?module? at startup.

Thanks again for all the help.

---

