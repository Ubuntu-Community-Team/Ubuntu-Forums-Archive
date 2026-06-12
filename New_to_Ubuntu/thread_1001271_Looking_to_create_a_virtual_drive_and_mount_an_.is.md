---
title: "Looking to create a virtual drive and mount an .iso"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Shadow_2014 on 2008-12-03
I'm wondering whether there's a program in adept, or one I can download that acts as Alcohol did. I wold like to create one or more virtual drives and mount images to them. Is there one program that does both? I'm also looking for the absolutely most user friendly interface.

---

### Post by sdowney717 on 2008-12-03
virtualbox

you use this to mount iso in a virtual machine

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by anewguy on 2008-12-03
I've never used it, so I can't just recommend it, but here is one solution I found on the net:

[http://http://onlyubuntu.blogspot.com/2007/12/gmount-iso-is-small-tool-written-using.html]("http://http://onlyubuntu.blogspot.com/2007/12/gmount-iso-is-small-tool-written-using.html")

if you do a yahoo or google search with the search string Ubuntu mount iso several hits are there which may be able to help you.

Dave ;)

---

### Post by C. Wizard on 2008-12-03
VirtualBox, but don't use the one the repositoires. Download the PUEL version directly from Sun.

---

### Post by anewguy on 2008-12-03
> **sdowney717 said:**
> virtualbox

you use this to mount iso in a virtual machine

If wanting to run a virtual machine this is truely valid and the iso is visible only to the virtual machine.  however, if wanting to simply mount and iso image in Linux without burning a CD/DVD, there are tools available to do that.  Using a vm would not work for that desire.

Dave ;)

---

### Post by C. Wizard on 2008-12-03
You can install an ISO image in VirtualBox without having to burn a CD/DVD.

---

### Post by anewguy on 2008-12-03
> **C. Wizard said:**
> You can install an ISO image in VirtualBox without having to burn a CD/DVD.


Yes you can, however unless something has changed, that mounted iso is only visible inside of a virtual machine.  For a person simply wanting to mount an iso image in Linux, that wouldn't work and other solutions are available.

Dave ;)

---

### Post by DGortze380 on 2008-12-03
He's not talking about a virtual machine!

he wants to mount an iso.

you can mount an iso with the mount command just like any other media/drive.

man mount

---

### Post by anewguy on 2008-12-03
> **DGortze380 said:**
> He's not talking about a virtual machine!

he wants to mount an iso.

you can mount an iso with the mount command just like any other media/drive.

man mount

Thank you!!!  Exactly the point I was trying to make!

dave ;)

---

### Post by DGortze380 on 2008-12-03
[http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2](http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2)

---

### Post by damis648 on 2008-12-03
yes.
```

mount -t iso9660 /path/to/iso /mountpoint
```

---

### Post by Shadow_2014 on 2008-12-03
That line of code won't work unless I have a mount point, right? And to have a mount point, I need a virtual drive. So, VirtualBox is the program I should seek for this? I'm just wanting to mount a Fallout iso so I can play without burning it or anything.

---

### Post by jimreynold2nd on 2008-12-04
nah, a mountpoint is just a regular directory created with mkdir...
Basically, you wont need any additional program to mount an iso in Ubuntu (or any *nix that support loop and iso9660)
the command I use is
```
sudo mount -t iso9660 -o loop /path/to/iso /path/to/where/you/want/it/to/mount
```

---

### Post by DGortze380 on 2008-12-04
> **Shadow_2014 said:**
> That line of code won't work unless I have a mount point, right? And to have a mount point, I need a virtual drive. So, VirtualBox is the program I should seek for this? I'm just wanting to mount a Fallout iso so I can play without burning it or anything.

No, forget about VirtualBox, it's a great program, but not what you want.

use mkdir to create a directory in /media named whatever you want, then use the mount command to mount the iso to that directory.

---

### Post by Rayaz on 2008-12-04
Gmountiso is the GUI program for mounting iso's. Isomaster for creating iso's. You will have to make a mount point like this: at the command prompt in terminal type "sudo mkdir /media/iso". This will create a mount point "iso"  which you can use in gmountiso. Hope this answers your question.

---

