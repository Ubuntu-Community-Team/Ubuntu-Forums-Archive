---
title: "recover data? usb stick"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by minsf on 2009-01-16
my 128MB usb disk-on-key doesnt work.
A) how to recover the data?
B) any idea why this happened?

_more details:_
1. my usb used to mount automatically on my ubuntu 8.10 and used to work properly. 
2. this morning i put it in an xp laptop, and it didnt work. so i checked the "properties" and it showed all space is used (i only used about 50%) and said its a "RAW" partition.
3. I "safely removed" it from the xp, and plugged it in the ubuntu laptop. alas, no auto mounting.
4. "sudo [COLOR="Red"]lshw[/COLOR]" gave me: ```
     *-scsi
          physical id: 2
          bus info: usb@1:1
          logical name: scsi12
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@12:0.0.0
             logical name: /dev/sdb
             size: 126MiB (132MB)
```
5. i tried to mount it manually with "[COLOR="Red"]sudo mount -t vfat /dev/sdb /media/disk[/COLOR]" (of course i "mkdir"ed the /media/disk before the mount command). i got an error. so i tried to change the filesystem option to "-t ntfs" and "-t autofs" and even "-t ext3". nada. i can post the errors upon request, but they mainly complained about the file system.
6. so i downloaded the testdisk package, and ran "sudo [COLOR="Red"]photorec[/COLOR]". i chose the drive, then i chose "INTEL/PC", then i chose "other" filesystems (that is not EXT2/EXT3). photorec couldnt carve anything. i can post here the options of the photorec upon request- i used the defaults (in particular, it searched for almost any file type).
7. then i had a nice idea (even you gurus that think it's lame, must admit it is nice for a newbie to think about it):```
sudo [COLOR="Red"]xxd /dev/sdb[/COLOR] /home/minsf/usb_bytes
``` hoping to capture the bytes from the usb stick. looking at the tail, i noticed that xxd carved 7dffff0+16 bytes, that is 7*16^6+13*16^5=132120576 bytes=126MiB precisely. this seems to be compatible with the advertising tricks of a usb-stick's manufacturer that sells "128MB". so i ran ```
cat /home/minsf/usb_bytes | [COLOR="Red"]grep -v "ffff ffff ffff ffff ffff ffff ffff ffff"[/COLOR]
```
and got nothing, meaning all bytes are ff, right?

so i guess my questions translate to:
A) is there still any hope with some other method?
B) how to make sure this doesnt happen again? (which is a simple consequence of the "why" question)

---

### Post by taurus on 2009-01-16
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by minsf on 2009-01-16
```
minsf@minsf-laptop:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3110    24981043+  83  Linux
/dev/sda2            3493        3648     1253070    5  Extended
/dev/sda3            3111        3492     3068415   83  Linux
/dev/sda5            3493        3648     1253038+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 132 MB, 132120576 bytes
5 heads, 51 sectors/track, 1011 cylinders
Units = cylinders of 255 * 512 = 130560 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by taurus on 2009-01-16
Just so you know, USB sticks, thumbdrives, or whatever you call them die more often than most people would think.  So if you value your data, use either the CD or DVD.

---

### Post by minsf on 2009-01-16
thanks for info. i've been using this one for a few years so i guess i counted on it more than i should have.
are external hard-drives also that unreliable? (that is, if they connect through the usb port)

---

### Post by minsf on 2009-01-17
bump. any other idea, before i give up?

---

### Post by veruus on 2009-01-17
> **minsf said:**
> bump. any other idea, before i give up?

Yep.  Make an image of the USB drive and we'll see if something can be recovered from it.

```
sudo dd if=/dev/sdb of=old_data.dd
sudo chown minsf:minsf old_data

       *note: minsf should be the username on the
        machine.  If your username is steve, use that
        instead.
```

What kind of data was on the drive?

---

### Post by minsf on 2009-01-17
mostly text files are the important data, but i had an old excel file, PDF and mp3s
dd and chown - done
now what?
by the way, thanks veruus

---

### Post by vanadium on 2009-01-17
> So if you value your data, use either the CD or DVD.
I wouldn't trust these too much neither.

---

### Post by minsf on 2009-01-17
> **vanadium said:**
> I wouldn't trust these too much neither.

do you trust external hard drives? (through usb)

---

### Post by vanadium on 2009-01-18
If one of the two hard drives break, I'll buy another and rsync a second copy to the new one. I have three copies for the most valuable stuff though (documents, pictures).

---

### Post by minsf on 2009-01-18
any more ideas how to recover my data? 
:(

---

### Post by veruus on 2009-01-19
> **minsf said:**
> any more ideas how to recover my data? 
:(


Yep.  Remember that file I had you create from your USB drive via *dd*?  You can scan it for recoverable data.  Install *testdisk*

```
sudo apt-get install testdisk
```

and then *man photorec* to see how to use it.  Run it from a terminal.  If you aren't sure what to do from here, make the file so that it can't be altered or deleted (-rw) and just experiment.  When you have recovered your data, make it so you can delete the file (+rw) and get rid of it.

Remember, Google is your friend.

---

### Post by minsf on 2009-01-20
thanks. i've already tried photorec on the usb itself. do u think running it on that file will yield a different result? hmmm... i'll give it a try.

---

### Post by veruus on 2009-01-20
> **minsf said:**
> thanks. i've already tried photorec on the usb itself. do u think running it on that file will yield a different result? hmmm... i'll give it a try.

Yeah, if you were able to copy the blocks from your device you should be in good shape.  If not - well, we tried.  :)

---

