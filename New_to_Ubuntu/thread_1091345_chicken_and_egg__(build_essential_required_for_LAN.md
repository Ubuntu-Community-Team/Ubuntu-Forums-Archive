---
title: "chicken and egg  (build essential required for LAN)"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-09
Hi forum,

still struggling here with various WLAN issues.

I've got instructions for installing wireless drivers. The machine doens't have a network connection but I do have a laptop connected to the net so I can download files.

The instructions for getting wireless drivers requires command line make, make install and patch. I understand that I need build essentials for that (although make does work without -> are there more than one issue of make).

I'm installing from unetbootin so I have a USB stick and no CD but the machine does have a CD rom. I also have a copy of the CD ISO that was used to make the USB stick.

There is loads of space on the machine so I could easily extract the ISO to a partition or leave it on the hard disk.

What is the best way to get build-essential on the machine (and potentially leave a place to get source files e.g. CD on the hard drive)? I don't want to leave a physical CD in the drive though.

I saw the following method for CD in a different forum but can't work out whether the drive appears as a second CD ROM or not

>    1. Use a CD writer to create a ISO image of the install CD. I keep mine as /var/Ubuntu_6.10_i386.iso
   2. Configure a mount point by editing /etc/fstab
      (/var/Ubuntu_6.10_i386.iso /media/Ubuntu_6.10_i386.iso udf,iso9660 noauto,loop). I also created the mount point mkdir /media/Ubuntu_6.10_i386.iso
   3. Truncate the file /var/lib/apt/cdrom.lists
   4. Add the line Acquire::cdrom::mount "/media/Ubuntu_6.10_i386.iso/"; to file /etc/apt/apt.conf
   5. Edit the /etc/apt/sources.list file and remove the references to the physical CD drive based source
   6. Run the command sudo apt-cdrom add


If I follow this, I'd hope the CD appears as a second and separate version. Otherwise, is there a way to put sources in a directory?

---

### Post by KIAaze on 2009-03-11
If I understood correctly, you want a way to install the build-essential package without internet access, right?

This should help:
[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

---

### Post by RichardCL on 2009-03-12
Thanks very much. That worked fine. It seems strange that build-essential isn't in the standard install. Especially if wireless drivers seem to all need them for installation.

What I was looking for was actually a way to store all the sources in one the hard disk so that installation without leaving the CD in the drive. In Windows XP it was possible to copy the i386 directory from the CD and change the registry to look in that path. I'd though it may be possible to add a copy of the Ubuntu ISO to the sources.list file or extract the ISO to a fresh partion and mount as CD. I didn't find a way to do that yet so far.

---

### Post by KIAaze on 2009-03-12
I'm not familiar with unetbootin, but have you tried this: [https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD)

And if you want to use an .iso on the hard disk as source, you can do this apparently:
```
sudo synaptic --add-cdrom /media/iso/ 
```
[http://ubuntuforums.org/showthread.php?t=381972](http://ubuntuforums.org/showthread.php?t=381972)

P.S: The reason build-essential is not included by default is probably because "normal users" aren't supposed to compile programs from source.
It's something for developers.
What did you have to compile? ndiswrapper is in the repositories. ;)
Perhaps you could have used:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.9
```

---

### Post by RichardCL on 2009-03-12
> **KIAaze said:**
> I'm not familiar with unetbootin, but have you tried this: [https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD)

And if you want to use an .iso on the hard disk as source, you can do this apparently:
```
sudo synaptic --add-cdrom /media/iso/ 
```
[http://ubuntuforums.org/showthread.php?t=381972](http://ubuntuforums.org/showthread.php?t=381972)



That is exactly what I was looking for. I've got a couple of machines without CD-ROM and only with wireless. Now I can use a USB stick for the install, copy the iso file and work from there.

The unetbootin is only a quick way from within either windows or Linux to make a Linux boot CD. It is a very good tool because it formats, makes bootable, installs a live-CD version and the necessary files for booting. You can select from a whole range of OS including Ubuntu, Kubuntu, Debain...

I worked with unetbootin from day one with Linux so I'm used to it and haven't looked for another way to do it.

> **KIAaze said:**
> 
P.S: The reason build-essential is not included by default is probably because "normal users" aren't supposed to compile programs from source.
It's something for developers.
What did you have to compile? ndiswrapper is in the repositories. ;)
Perhaps you could have used:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.9
```

I'd moved to Linux to get away from the protective environment that Windows creates, which stops me from doing things that I want to do. I pretty much work with the rule "read the manual thoroughly before typing sudo". I'm learning a lot and did have to reinstall once after screwing up a lamp-server install. However, with a good databackup, what coudl go really wrong?

I was trying to build the drivers for my wireless. I'm using the D-link DWA 140. It is based on the RT2870, which I purchased because Linux drivers are available. The only problem is that the free distribution of drivers is source code only and requires a few minor configuration, followed by "sudo make && sudo make install". That seems to require the build-essential package. Hence chicken and egg because the WLAN drivers are required to give the apt-get command access to the respositories.

---

### Post by KIAaze on 2009-03-12
> **RichardCL said:**
> "sudo make && sudo make install"
Should be just "make && sudo make install". Always minimize the use of sudo. But you probably already knew that. ^^

---

### Post by RichardCL on 2009-03-13
> **KIAaze said:**
> Should be just "make && sudo make install". Always minimize the use of sudo. But you probably already knew that. ^^

No, actually that's new. I thought make required admin rights but now I suppose it doesn't since nothing gets changed on the system. Always please to learn new stuff.

---

