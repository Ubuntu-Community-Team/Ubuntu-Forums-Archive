---
title: "SillySod Can't Access Floppy Drive"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by SillySod on 2009-04-13
I'm having a problem accessing my floppy drives.  I did get them working a while back, but now every time I put a disc in and try to mount it, terminal says:

```

mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and the file manager says:

```

mount: I could not determine the filesystem type, and none was specified.

```

I tried booting from DOS from an old system disc to read a disc and it read OK and it formatted OK, but going back to Xubuntu still gives the above errors.

I am using 720K DOS discs, which I need to format and read for use with old systems I use.

Can anyone help, I really need to be able to use floppy discs.

---

### Post by Jakey_TheSnake on 2009-04-13
Don't think I'll be able to help, but what's the output of 
```
dmesg | tail
``` 

Hopefully it'll be fairly intuitive.

---

### Post by SillySod on 2009-04-13
This is what it says:

```


[ 3550.305811] cont=f8d2366c
[ 3550.305811] current_req=f59bcd48
[ 3550.305811] command_status=-1
[ 3550.305811] 
[ 3550.364139] floppy0: -- FDC reply error<3>FAT: invalid media value (0x64)
[ 3553.115457] VFS: Can't find a valid FAT filesystem on dev fd0.
[ 3566.012257] FAT: invalid media value (0x64)
[ 3566.012269] VFS: Can't find a valid FAT filesystem on dev fd0.
[ 3572.528227] FAT: invalid media value (0x64)
[ 3572.528240] VFS: Can't find a valid FAT filesystem on dev fd0.


```

I've just discovered that I can format and read HD 1.44MB floppy discs, but not 720K DD ones.  I'm not sure if I have tried 720K discs before today.

When I format, every disc gives me an error just after verification begins saying "Bad data at cyl 0" but continues and verifies OK for the rest of the disc, and writing the filesystem with mkfs.msdos works.  It's just when trying to mount and access the disc that the problems start.

---

### Post by Sir Jasper on 2009-04-13
Hi,

To mount a floppy > go to places after:
    sudo modprobe floppy

It worked for me with 8.10

My regards

---

### Post by Jakey_TheSnake on 2009-04-13
[This](http://manpages.ubuntu.com/manpages/jaunty/en/man4/fdc.4freebsd.html) is all I could find, sorry. 

If you dual-boot with Windows I believe you can use Winimage, though. 

Sorry! I guess 720K floppy's are too old school for the internet. 

Surely your 'old' systems can take 1.44MB floppys?

---

### Post by SillySod on 2009-04-13
I tried changing the floppy drive in my BIOS to 720K but that didn't work either.  I can use 1.44MB floppies fine, but it just doesn't seem to like 720K ones.

I need to be able to write (and occasionally read) double-density discs either in DOS format or certain other special formats for the old systems I tinker about with.  They can only cope with double-density discs, not high density, and I used to be able to do this on Windows on the same machine.

---

### Post by SillySod on 2009-04-28
This little bit of trickery has solved the problem:

```

sudo mknod -m 0660 /dev/fd0d720 b 2 24

```

Then I can use 720K floppy discs using the new device created:

```

sudo fdformat /dev/fd0d720
sudo mkfs.msdos /dev/fd0d720

```

---

