---
title: "Dual  boot help"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Sl33py on 2010-10-23
So, i had a dual boot setup (ubuntu and xp) and then i had to reinstall the windows and now the boot menu is gone. Ubuntu was installed in a spereate partition (ext3). Is there anyway i can run dual boot again without the ubuntu cd?

---

### Post by Hippytaff on 2010-10-23
Which one has gone from the boot menu? if it's windoze

boot from liveCD...if you know what partitions are what you need to mount root (and boot if you have a seperate boot partition.

```

sudo mount /dev/sda? /mnt

```where ? is the root partition. (you can type sudo fdisk -l in terminal to see the partitions, root is normally sda5)

Mount the rest of your devices

```

sudo mount -- bind /dev /mnt/dev

```then in terminal

```

sudo chroot /mnt

``````

update-grub

``````

grub-install /dev/sda

```This should bring back the option to boot into ubuntu :-)

---

### Post by Sl33py on 2010-10-23
I can only use windows at the moment... The problem is i don't have the ubuntu cd/usb, guess i will just download it..

---

### Post by ivarn on 2010-10-23
so u don't have a live cd?
u really should take a dvd backup once in awhile.
But ok, in windows, go to [www.download.com](www.download.com) and download auto super grub.
It's a free app that will let you set up a grub menu automatically.
When you come back to ubuntu, run this command:
```
sudo apt-get install grub2
```
Good luck :)

---

### Post by sikander3786 on 2010-10-23
EasyBCD, a Windows based global bootloader here.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Grub is a far better and superior choice in my opinion. EasyBCD is not that bad either.

If you don't have a Live CD, you can use this loader to boot into Ubuntu and then decide if you want to keep it or reinstall Grub from within the Ubuntu install.

---

### Post by Hippytaff on 2010-10-23
> **ivarn said:**
> so u don't have a live cd?
u really should take a dvd backup once in awhile.
But ok, in windows, go to [www.download.com]("http://www.download.com") and download auto super grub.
It's a free app that will let you set up a grub menu automatically.
When you come back to ubuntu, run this command:
```
sudo apt-get install grub2
```Good luck :)

good advice....but you can download the ubuntu iso at the ubuntu website, it's always worth keeping a ubuntu liveCD around :-)

but the supergrub is always worth having too :-)

---

### Post by Sl33py on 2010-10-23
Auto super grub is giving some error about unrecognized partition and the easy bcd isnt working...

---

### Post by sikander3786 on 2010-10-23
Why is EasyBCD not working? Any error there? Did you see this wiki page.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Hippytaff on 2010-10-23
> **Sl33py said:**
> Auto super grub is giving some error about unrecognized partition and the easy bcd isnt working...

try the ubuntu liveCD and then you should be able to open terminal and do the mounting and updateing of grub from there

---

### Post by ivarn on 2010-10-23
> **Hippytaff said:**
> try the ubuntu liveCD and then you should be able to open terminal and do the mounting and updateing of grub from there
He said he doesn't have one.

BUt yea, login to windows and burn a copy.

---

### Post by Sl33py on 2010-10-23
EasyBCD isn't even starting it gives a "failed to initialized properly" error. I am downloading the live cd though.

---

### Post by Hippytaff on 2010-10-23
> **Sl33py said:**
> EasyBCD isn't even starting it gives a "failed to initialized properly" error. I am downloading the live cd though.

It is probably easier to do it from liveCD or USB :-)

---

### Post by Sl33py on 2010-10-24
So, i reinstalled grub following what #2 said and now there is no option to select windows..

---

### Post by Hippytaff on 2010-10-24
try this - boot from live cd. Open a Terminal

```

sudo fdisk -l

```Find the name of the root partition (eg sda5) if you've got a seperate boot partition you need the name of that too.

do
```

sudo mount /dev/sda5 /mnt

```(and the same for the boot partition if you have one)
Then
```

sudo mount -- bind /dev /mnt/dev

``````

sudo chroot /mnt
update grub
grub-install /dev/sda

```hopefully that should do it. Restart.

let me know how it goes

---

### Post by Sl33py on 2010-10-24
```
sudo mount -- bind /dev /mnt/dev
``` Running this results in a wall of text 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Edit: I just restarted and i got the option for windows, it is working fine now, Thanks for the help.

---

### Post by Hippytaff on 2010-10-24
Sorry

```

mount --bind /dev /mnt/dev

```
--bind not -- bind

my mistake :-s

---

