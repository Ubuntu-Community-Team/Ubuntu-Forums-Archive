---
title: "Can't mount disk drive when CD is inserted"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-19
Hi so I have a CD-RW/HD-DVD Drive (don't laugh) and I have put in my Lock On: Modern Air Combat CD into the drive to see if I could install it using WINE (I checked winehq and it says it should work).

But when I insert it it spins round for a bit and then I try to open the disk drive under Computer and it tells me:

> 
Unable to mount location

Can't mount file


Any ideas why this wouldn't be working? Is it because it is a windows game CD? Audio CDs seem to work okay.

---

### Post by MaindotC on 2009-03-19
The cd should be in .iso format which is independent of the data on it.  It may be your drive - not sure how well it is supported - you may want to check the linux/ubuntu hardware compatibility list.  It's good that you posted your specs in your signature, but please hotlink them to the manufacturer's specifications sites like mine are.

With the cd in the drive, please post the output of:
```

sudo fdisk -l /dev/scd0

```
where /dev/scd0 is your optical drive - change that depending on how your system names the optical drive.

---

### Post by humphreybc on 2009-03-20
Where would I find what my Computer names my drive?

---

### Post by MaindotC on 2009-03-20
Just type
```

sudo fdisk -l

```
and one of them will be your optical drive.  I was just trying to narrow down the possibilities for you.

---

### Post by humphreybc on 2009-03-20
```


sbenjamin@benjamin-laptop:~$ sudo fdisk -l
[sudo] password for benjamin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156286964    7  HPFS/NTFS

```

That's all I have... don't see anything about a disk drive there. I don't have the disk in the drive at the moment, it's at home.

---

### Post by MaindotC on 2009-03-20
Well when you plug in the usb drive it will show on this output.  Just post the output with the usb drive plugged in and you'll see the difference.

---

### Post by humphreybc on 2009-03-20
It's a disk drive inside the laptop that is the problem...

---

### Post by MaindotC on 2009-03-20
Oh sorry - confused this w/ another thread.  Just put any disk in the optical drive and then run the fdisk command again.

---

### Post by MaindotC on 2009-03-20
My fault - fdisk is for different media.  Can you post the output of:
```

ls /dev/s*

```

---

### Post by newbee70 on 2009-03-20
I believe you could use the terminal command. once you have the cd/dvd in the drive.

mount


to see your cd/dvd rom drive, you may have to use the following.

sudo mount

---

### Post by MaindotC on 2009-03-20
Yes, in my case my machine identifies my optical drive as /dev/scd0 so I can mount it using:
```

sudo mount /dev/scd0 /media/cdrom -t iso9660 -o loop

```
and there's an entry in my /etc/fstab file that defines this so I don't have to type it each time I boot or insert a cd:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d6088750-972e-4ed8-a9eb-074a8eeb251f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5cd721ed-86bc-4c6c-9ecc-c9ec2bcf3df3 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/disk 	ext3	defaults	0	0

```
The part that starts with /dev/scd0 is relevant to this situation.

---

### Post by humphreybc on 2009-03-20
```

benjamin@benjamin-laptop:~$ ls /dev/s*
/dev/scd0  /dev/sda2  /dev/sdb1        /dev/sg0  /dev/snapshot  /dev/stderr
/dev/sda   /dev/sda5  /dev/sequencer   /dev/sg1  /dev/sndstat   /dev/stdin
/dev/sda1  /dev/sdb   /dev/sequencer2  /dev/sg2  /dev/sr0       /dev/stdout

/dev/shm:
pulse-shm-2011475657

/dev/snd:
controlC0  controlC1  pcmC0D0c  pcmC0D0p  pcmC1D3p  seq  timer

```

That's the output. I'll try it with the disk in the drive tonight. It has been doing some odd things recently... like showing up under "Computer" as a CD Drive, or not showing up at all. Sometimes when I put in a DVD it spins and spins for ages but nothing ever comes up and the drive will disappear from the list under "Computer." It also is not burning disks, failing pretty much all the time.. I think the drive is broken.

---

### Post by humphreybc on 2009-03-21
I took the laptop apart and checked the connections on the disk drive and they all seemed fine. I got rid of some dust that was in there but apart from that everything looked in good condition.

I put it back together and inserted a genuine, non-scratched audio CD and it played fine with sound-juicer, although under "Computer" I had two listings for audio CDs... (see attached screenshot.)

When I inserted a brand new DVD it was a different story, however. I put in "Rock N Rolla" to see what happened and it recognized the disk and placed an icon on my desktop called "ROCKNROLLA" but when I autoran the DVD under VLC media player, and nothing happened. I then tried another DVD player, Ogle, to see if that would make a difference and it didn't. It won't play the disk at all.

I tried another DVD, "Body of Lies" to see if that would play. Same thing happened, it recognised the disk and opened VLC player - this time the window opened and it flickered for a couple of times on a black screen and then it stopped after about 2 seconds. The drive kept spinning for a further 15 seconds then went quiet. Ogle had no luck either.

This is the output of the two commands with the disk in the drive:

```

benjamin@benjamin-laptop:~$ ls /dev/s*
/dev/scd0  /dev/sda2  /dev/sdb1        /dev/sg0  /dev/snapshot  /dev/stderr
/dev/sda   /dev/sda5  /dev/sequencer   /dev/sg1  /dev/sndstat   /dev/stdin
/dev/sda1  /dev/sdb   /dev/sequencer2  /dev/sg2  /dev/sr0       /dev/stdout

/dev/shm:
pulse-shm-4086793934  pulse-shm-425392018  pulse-shm-91467415

/dev/snd:
controlC0  controlC1  pcmC0D0c  pcmC0D0p  pcmC1D3p  seq  timer
benjamin@benjamin-laptop:~$ sudo fdisk -l
[sudo] password for benjamin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156286964    7  HPFS/NTFS

```

What do you think it is? Under Windows I could play DVDs fine, although the drive did not burn CDs or DVDs. It crapped out after about 25% burning. Is the drive dying or is it a driver problem?

---

### Post by MaindotC on 2009-03-21
Looks like /dev/scd0 is your optical drive.  Try mounting it manually as I suggested.  If that doesn't work could you see if there's a firmware upgrade for your drive?  If not, can you try a different drive?

Edit: Just saw your post.  I'm not sure why it's mounting the cd drive under the "Computer" icon.  Can you move the "Computer" icon just to be certain it's not covering the optical drive icon?  Also, can you post the contents of /etc/fstab and /etc/mtab please?

---

### Post by humphreybc on 2009-03-21
Hey I just put in Lock On (which is what I was having problems with before) and it has showed up properly and mounted. I am going to run the .exe under Wine to see if I can install it.

I can't really use another drive as it is a laptop disk drive, and I would have to find another one to fit to replace it with.. are they all the same size in laptops?

---

### Post by egalvan on 2009-03-21
> **humphreybc said:**
> 
I can't really use another drive as it is a laptop disk drive, and I would have to find another one to fit to replace it with.. are they all the same size in laptops?

Laptop drives are two basic thicknesses... the slim ones are not too common.
I believe the measurements are approx 12mm thick and 9mm thick...
not really a large difference...
but I am probably remembering these wrong...

The connection is either PATA IDE (one connector), or SATA on the newer ones.

The big problem is the front face plate...

Most every laptop seems to have it's own version, usually with curves or angles, or cutouts.
The placement of the LED, button and ejector hole are also variable.

The faceplates are almost always removable,
and if you are lucky to have a flat, rectangular one,
 then no changes are needed.

The drive may (probably does) have mounting rails, or different connector attached to the drive. These are  attached by screws or tabs. Don't lose the screws, they are difficult to replace...

---

### Post by MaindotC on 2009-03-21
Hopefully the situation is somewhat resolved.  I just hope he can wine his game.

---

### Post by humphreybc on 2009-03-22
> **strAlan said:**
> Hopefully the situation is somewhat resolved.  I just hope he can wine his game.

Sort of. Some things work... like it seems to be playing Audio CDs okay but I am still concerned about it not playing DVD movies.

I tried two games with Wine and neither worked haha.

---

### Post by MaindotC on 2009-03-22
DVD movies - did you install libdvdcss2 from the ubuntustudio repository?  You need that to play dvds!!

---

### Post by humphreybc on 2009-03-22
Ha! That fixed it... far out. hahaha. I'll check if it burns discs tomorrow when I get some more blank CDs.

---

### Post by MaindotC on 2009-03-22
Omfg why do I always make things so much more complicated than they are...

---

### Post by humphreybc on 2009-03-22
Haha yeah. It'll be interesting to see if it burns CDs and DVDs now!

---

### Post by egalvan on 2009-03-23
Also, check to see if you have the third-party repo's enabled...
especially medibuntu

---

