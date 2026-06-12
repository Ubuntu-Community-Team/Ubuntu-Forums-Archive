---
title: "iTunes support"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by justcruising on 2009-11-10
Hey is it possible to install iTunes on 9.10 without using any emulators or virtual software. On another note when i installed linux i chose the option that automatically mounts with windows. Now when i save something in linux it is saving directly to the vista partition, is there anyway to remove the vista partition from being mounted?

---

### Post by alphacrucis2 on 2009-11-10
> **justcruising said:**
> Hey is it possible to install iTunes on 9.10 without using any emulators or virtual software.

No. You can run some version of Itunes under Wine which you might regard as an emulator but I gather they don't run at all well:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

If Apple wanted to, they could port Itunes to run on Linux with less effort than they put in to port it to Windows but I doubt they will ever do it. 

> 

 On another note when i installed linux i chose the option that automatically mounts with windows. Now when i save something in linux it is saving directly to the vista partition, is there anyway to remove the vista partition from being mounted?

I presume this must be because it is getting mounted via fstab. To have a look:

```
cat /etc/fstab
```

---

### Post by ukripper on 2009-11-10
alphacrucis2 is right. You can't run itunes properly in ubuntu but you have alternative. See this link - [http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by justcruising on 2009-11-10
> **alphacrucis2 said:**
> No. You can run some version of Itunes under Wine which you might regard as an emulator but I gather they don't run at all well:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

If Apple wanted to, they could port Itunes to run on Linux with less effort than they put in to port it to Windows but I doubt they will ever do it. 



I presume this must be because it is getting mounted via fstab. To have a look:

```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=80097331-a3a5-4bb3-ac5b-6a8f9b3ec02d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7c616893-5e21-4e3c-b856-46dbc908d882 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thats my fstab

Its a pitty about iTunes i use it for my iPhone, guess i have to keep windows then :(

---

### Post by ukripper on 2009-11-10
> **justcruising said:**
> 
Its a pitty about iTunes i use it for my iPhone, guess i have to keep windows then :(

or perhaps use something which works with ubuntu.

---

### Post by justcruising on 2009-11-10
> **ukripper said:**
> or perhaps use something which works with ubuntu.

does that mean you have a suggestion lol. only reason i wanted iTunes is because it would allow me to sync applications that i download

---

### Post by ukripper on 2009-11-10
> **justcruising said:**
> does that mean you have a suggestion lol. only reason i wanted iTunes is because it would allow me to sync applications that i download

Just for syncing you can use gtkpod or amarok.
Check info here - [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by justcruising on 2009-11-10
> **ukripper said:**
> Just for syncing you can use gtkpod or amarok.
Check info here - [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

cheers man will look into that for sure.

you got any ideas about fstab, i got no idea when it comes to that stuff

---

### Post by Rayve on 2009-11-10
> **justcruising said:**
> cheers man will look into that for sure.

you got any ideas about fstab, i got no idea when it comes to that stuff

I'm not positive about fstab (which stands for "filesystem tables", btw) but I don't think I see any FAT32 (vfat, in linux) or HPFS/NTFS which Windows uses.  I believe this would mean that your Windows partition isn't mounted.

What does 

```

fdisk -l

```return? (That's "fdisk <hyphen><lower case L>) You may need to run it as root using "sudo" at the start and then enter your password when prompted (it won't show anything when you enter your password).

ETA: You can also check out the guide in my signature for more info. :)

---

### Post by SunnyRabbiera on 2009-11-10
> **justcruising said:**
> does that mean you have a suggestion lol. only reason i wanted iTunes is because it would allow me to sync applications that i download

Yeh for a iphone you may want to dualboot or install windows in a virtual machine, linux cannot really control what apple does so support for some stuff is very loose.
As is the case for most hardware/software.
The issue with linux is that most devices out there only have windows in mind, OSX is there too but linux is dead last in terms of official support from vendors.
But the linux developers do their best, but they can only do so much on their own.

---

### Post by aaycumi on 2009-11-10
You can download and install PlayonLinux, from the Ubuntu Software centre under games. This automates a lot of the usual fiddling around with wine you have to do.
It does have a version of iTunes in there (7.7.12 or something like that) so its a good place to start and PlayonLinux does most the work for you.

---

### Post by SunnyRabbiera on 2009-11-10
> **aaycumi said:**
> You can download and install PlayonLinux, from the Ubuntu Software centre under games. This automates a lot of the usual fiddling around with wine you have to do.
It does have a version of iTunes in there (7.7.12 or something like that) so its a good place to start and PlayonLinux does most the work for you.

playonlinux is a good suggestion, it might not install the latest version of itunes but its fine.
Me I hate itunes so good riddance if you ask me.
But I dont have an iphone or ipod, thank goodness I dont too.

---

### Post by ukripper on 2009-11-10
> **SunnyRabbiera said:**
> 
But I dont have an iphone or ipod, thank goodness I dont too.

+1... I am going to get G1 or Palm pre soon

---

### Post by banerjeerupak on 2009-11-10
can i use the same for syncing with iPod?

---

### Post by ukripper on 2009-11-10
> **banerjeerupak said:**
> can i use the same for syncing with iPod?

Yes gtkpod works perfectly with ipod syncing

---

### Post by landtodd on 2009-11-10
I speak only of iPod support.  I don't know anything about iPhone!

A terrific thing about "Ubuntu World" is you can try iTunes replacements without ever buying (or committing to) them.  Go ahead and try Rythmbox and/or gPodder, and let us know what *you* think!  To me, Rythmbox appears to work more like iTunes.  By contrast, gPodder is a joy!  

After I appropriated a little-unused 80-gig iPod Classic (terrific hardware!), I begrudgingly kept a Windows PC around, just to run iTunes.  Until the exact day I found gPodder.  (That PC is now happily chugging away with Ubuntu 9.10.) 

One great thing about most open-source iTunes replacements is the ability to export and import podcast-directory OPML files.  I was never able to do that reliably with secretive, closed-source iTunes.

If you try gPodder, you may have to initialize the connection to your iPod using gtkpod directly.  (I'm sure that's something they're working on.)  You'll have to tell gPodder that you have an iPod, and that it mounts at /mnt/<first 11 chars of your iPod's name>.  Works like a charm after that.

Even amongst Windows programs, iTunes is a dog.  Huge, slow, counter-intuitive.  It was always my fault -- for wanting to do things the way I wanted to do them -- but I lost my podcast directory several times, and lots of music with iTunes.  If a person *really* wants to spend money on mp3s, they'll need to stick with iTunes.  There are unrelenting opportunities to spend money at the iTunes store!

---

### Post by landtodd on 2009-11-10
"/mnt/<first 11 chars of your iPod's name>. "

That may be /dev or some first node other than /mnt.  gPodder defaults to the right one.  (I don't have my Ubuntu box here to check.)

---

### Post by justcruising on 2009-11-12
> **aaycumi said:**
> You can download and install PlayonLinux, from the Ubuntu Software centre under games. This automates a lot of the usual fiddling around with wine you have to do.
It does have a version of iTunes in there (7.7.12 or something like that) so its a good place to start and PlayonLinux does most the work for you.

Thanks i will give that a try

---

### Post by justcruising on 2009-11-12
> **Rayve said:**
> 

What does 

```

fdisk -l

```return? (That's "fdisk <hyphen><lower case L>) You may need to run it as root using "sudo" at the start and then enter your password when prompted (it won't show anything when you enter your password).

ETA: You can also check out the guide in my signature for more info. :)

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5950    47793343    7  HPFS/NTFS
/dev/sda3            5951        9729    30354817+   5  Extended
/dev/sda5            5951        7591    13181301   83  Linux

---

