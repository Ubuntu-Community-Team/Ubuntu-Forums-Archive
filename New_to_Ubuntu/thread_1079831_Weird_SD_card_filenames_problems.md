---
title: "Weird SD card filenames problems"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by kaspar_silas on 2009-02-24
Hi all,

Maybe someone can shed light on my recent problem. I have an asus 900 running 8.10 ubuntu. I have been using an SD card to extend my memory.

Just now I booted up and got madness when I tried looking at the files in nautilus. Just loads of empty boxes and weird shapes under the executable file icon. So I went to terminal and ran ls on the directory to get this

```

ls: cannot access /media/DRACOLA/My-Talks//./: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/	/.
                                                   /: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks//./: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks//./: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/!/.#/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/)/.+/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/1/.3/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/9/.;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/A/.C/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/i/.K/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/Q/.s/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/y/.[/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/a/.c/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/i/.k/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/q/.s/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/y/.{/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/ü/.â/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/ë/.ï/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/æ/.ô/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/ö/.¢/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/í/.ú/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#8976;/.½/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9618;/.&#9474;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9571;/.&#9559;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9524;/.&#9500;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9556;/.&#9574;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9572;/.&#9561;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#9496;/.&#9608;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/ß/.&#960;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#920;/.&#948;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/±/.&#8804;/: No such file or directory
ls: cannot access /media/DRACOLA/My-Talks/&#8729;/.&#8730;/: No such file or directory
&#9524;-?.&#9500;-?  &#9618;-?.&#9474;-?  ?/?.?/?  10?.30?  æ.?.ô.?              Motion    ü-?.â-?
&#9524;/?.&#9500;/?  &#9571;-?.&#9559;-?  ?.?.?.?  1/?.3/?  ë-?.ï-?              Nano      ü/?.â/?
&#9524;.?.&#9500;.?  &#9556;-?.&#9574;-?  ?/?.?/?  1.?.3.?  ë/?.ï/?              ö-?.¢-?   ü.?.â.?
&#9496;-?.&#9608;-?  &#9572;-?.&#9561;-?  ?.?.?.?  4DCBCT   ë.?.ï.?              ö/?.¢/?   y/?.[/?
&#9496;/?.&#9608;/?  &#8729;-?.&#8730;-?  ?/?.?/?  9/?.;/?  Fundie               ö.?.¢.?   y/?.{/?
&#9496;.?.&#9608;.?  &#9618;/?.&#9474;/?  ?.?.?.?  9.?.;.?  Highly-Charged-Ions  Outreach  y.?.[.?
!/?.#/?  &#9571;/?.&#9559;/?  &#8976;-?.½-?  90?.;0?  i0?.k0?              q0?.s0?   y.?.{.?
!.?.#.?  &#9556;/?.&#9574;/?  &#8976;/?.½/?  a0?.c0?  i0?.K0?              Q0?.s0?   y0?.[0?
)/?.+/?  &#9572;/?.&#9561;/?  &#8976;.?.½.?  A0?.C0?  i/?.k/?              q/?.s/?   y0?.{0?
).?.+.?  &#8729;/?.&#8730;/?  !0?.#0?  a/?.c/?  i.?.k.?              q.?.s.?   &#920;-?.&#948;-?
±-?.&#8804;-?  &#9618;.?.&#9474;.?  )0?.+0?  a.?.c.?  i/?.K/?              Q/?.s/?   &#920;/?.&#948;/?
±/?.&#8804;/?  &#9571;.?.&#9559;.?  ?0?.?0?  A/?.C/?  i.?.K.?              Q.?.s.?   &#920;.?.&#948;.?
±.?.&#8804;.?  &#9556;.?.&#9574;.?  ?0?.?0?  A.?.C.?  í-?.ú-?              ß-?.&#960;-?
?/?.?/?  &#9572;.?.&#9561;.?  ?0?.?0?  æ-?.ô-?  í/?.ú/?              ß/?.&#960;/?
?.?.?.?  &#8729;.?.&#8730;.?  ?0?.?0?  æ/?.ô/?  í.?.ú.?              ß.?.&#960;.?

```

what does this all mean? Can I recover the images files? Anyone any ideas?

---

### Post by llamabr on 2009-02-24
It's a font problem, I think.  What kind of files are they?  Can you still view them, or whatever they're supposed to do, even with the weird boxes?

cd to the directory, and run

```
file *
```

and post the output of some of it, if it's long, or all of it, if it's short.

---

### Post by cariboo on 2009-02-24
I get the same thing when formatting usb thumb drives using gparted.

Jim

---

### Post by kaspar_silas on 2009-02-25
I ran file *

it gives a long output along the lines of

```
directory
ERROR: cannot read `TimeFiel.d' (Input/output error)
ERROR: cannot read `tton.0' (Input/output error)
ERROR: cannot read `tton.N' (Input/output error)
ERROR: cannot read `U±.' (Input/output error)
ERROR: cannot read `U&#8729;.' (Input/output error)
data
ERROR: cannot read `x.' (Input/output error)
data
data
ERROR: cannot read `yBox._' (Input/output error)
ERROR: cannot read `z.U&#8776;' (Input/output error)
ERROR: cannot read `.&#931;' (Input/output error)
```

---

### Post by geirha on 2009-02-25
Looks like the filesystem may be corrupted. I think it's a good idea to run a filesystem check on it. To do that, first identify the device name of the card's partition. run the following in a terminal ```
mount
```
It will list all currently mounted filesystems, look for the line corresponding to your sd card. It should look something like
```
/dev/sdb1 on /media/DRACOLA type ext3 (rw)
```
The name you want to know is the first part, which I'm just guessing is /dev/sdb1.

Unmount the drive
```
sudo umount /media/DRACOLA
```
If you get a message saying it is busy, make sure there's no programs using it, close any file browser that is looking at /media/DRACULA and any terminal that is cd'ed into /media/DRACULA, and try unmounting again.

Now run the filesystem check, replace /dev/sdb1 in the command with the one you saw in the output of mount.
```
sudo fsck /dev/sdb1
```

Reboot and see if that made a difference.

---

### Post by kaspar_silas on 2009-02-25
> **geirha said:**
> 
Now run the filesystem check, replace /dev/sdb1 in the command with the one you saw in the output of mount.
```
sudo fsck /dev/sdb1
```

Reboot and see if that made a difference.

fsck told me the FATs differ but appear to be intact.
then found a whole host of files and names it reckons are bad.

But I don't really want to delete these yet. So I searched about for some recovery stuff. The photorec program seemed the thing so I am running that. Then after that I guess I use gparted to fix the drive.

Bit annoying this. It there anything I can do to stop this happening in future or is it a random, bad luck thing.

---

### Post by geirha on 2009-02-25
photorec sounds like a good idea. Also consider connecting the sd card to another computer (with enough space) and use ddrescue to create an image of the card. Then you can run photorec, fsck and other recovery tools on that without damaging the filesystem on the sd card any further.

After you've managed to recover your files, I recommend you format it with ext3 which should be more resiliant than the ancient FAT filesystem.

---

### Post by kaspar_silas on 2009-02-25
The saga continues ... 

I have removed all the files I need. So I thought I would reformat the SD card to the ext type as you suggested.

However I don't seem to be able to. Gparted can see the drive when mounted. But if I unmount it and try to start gparted, gparted just freezes at the scanning stage start. If I try to unmount the drive in gparted then it freezes as well.

Is there a different formatting technique. Or some global delete I can do before formatting. rm -rf /media/DRIVE must fails says it is read only

---

### Post by geirha on 2009-02-25
unmounting it through the gui also "ejects" it, I believe. By ejecting I mean it also unloads the driver for it. Have the card mounted automatically, then in a terminal use the umount command to unmount it.
```
sudo umount /dev/sdb1
```

See if you can get gparted to partition it now.

---

### Post by kaspar_silas on 2009-02-25
The manual unmount worked okay but gparted still freezes on lauch. If I physically eject the card it works just not if it's in and unmounted when gparted runs.

I tried to force mount the card to delete the files with:

sudo mount /dev/sdc1 /media/tu -o rw,force

but that gave me:

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If I look where it says:

[  128.188381] FAT: Filesystem panic (dev sdc1)
[  128.188505]     invalid access to FAT (entry 0x2d960010)
[  128.188562]     File system has been set read-only
[  397.099153] FAT: Unrecognized mount option "force" or missing value

I don't know what that means but it smells bad.

---

### Post by geirha on 2009-02-25
Ok, I guess we can try fdisk then. Fdisk is unfortunately not so easy to use, and it is a cli-only application, but generally works where other fails.

First of all unmount like before ```
sudo umount /dev/sdc1
``` In your previous post you used /dev/sdc1, so I'll assume your sd card is /dev/sdc. Make very sure that you use the correct device. Running ```
sudo fdisk -l
``` will display all harddrives and partitions, so you should be able to find the correct device name from there based on the size. I'll assume /dev/sdc is the sd card for the remainder of this post, so make sure you replace all occurances of /dev/sdc with the correct device name if it's a different one.

Make sure no partitions on /dev/sdc is mounted. If the following does not print anything, then no partitions on /dev/sdc is mounted 
```
mount | grep /dev/sdc
```

Start fdisk on the sd card
```
sudo fdisk /dev/sdc
```
1 Type p to print the current partition table
2 Type d to delete the partition
```

Command (m for help): d
Selected partition 1

```
3 Type p again, and the partition table should now be empty
4 Type n to add a new partition
4.1 It will ask whether it should be a primary or extended partition. Type p for primary partition
4.2 It will ask what partition number to use. Type 1 to create /dev/sdc1
4.3 It will ask where the partition should start. Hit enter for the default (beginning of disk)
4.4 It will ask where the partition should end. Hit enter for the default (end of disk)
```

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1023, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1023, default 1023): 
Using default value 1023

```
5 Type p to see that the new partition is listed
6 We are done. Type w to write the partition table to disk and exit.

Unlike gparted, fdisk does not format the new partition, so we need to do that manually with mkfs.ext3.
```
sudo mkfs.ext3 -L DRACOLA /dev/sdc1
```
The -L option sets the filesystem volume. Setting it to DRACOLA will make it mount at /media/DRACOLA (like the previous system did)

Now try taking the SD card out, and then back in to see that it gets mounted automatically to /media/DRACOLA. If it does, you're almost done. Unlike FAT, ext3 has ownership and permissions on files, so you'll need to change the ownership from the default (root) to your user.
```
sudo chown -v $USER:$USER /media/DRACOLA
```

Phew.

---

### Post by kaspar_silas on 2009-02-25
Geirha you are a legend, thanks alot. Lovely stuff to know for he future, plus you saved me a SDHC card. I actually had the shop sites open.

Actually the "prescription" didn't quite work first time. It failed to mount after the reformat saying something about the superblock. But I formatted again, restarted and all fell into place.

Im off to bed but again thanks

---

