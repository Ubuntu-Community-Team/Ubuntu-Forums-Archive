---
title: "230mb updates"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by dimitriv on 2009-02-23
hi, 
i've installed 8.1 (it looks great, thanks!), it now wants to download 230mb of updates. Two things
i. i expect to reinstall the OS a bunch of times as i'm trialling it
ii. using XP and Internet Download Manager I get quick downloads

1. Can I download these updates and store them so i don't have to download everytime i rebuild?
2. Can i download the updates using IDM (ie. not via the Ubuntu auto update mechanism)?

Thanks in advance

---

### Post by binbash on 2009-02-23
yes you can store that downloads at usb drives and you can install them.(there is also an app called apt-zip but i didn't try it) , yes you can add it to idm and download packages(but you have to add each package :D )

---

### Post by geirha on 2009-02-23
In synaptic, you can mark all updates for install, then go to File -> Create package download script (or something like that). The script it creates will use wget to retrieve each package. You probably just need to replace wget with idm. See [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript) for more information.

And APTonCD might be just what you need for storing those updates
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

### Post by Doug11 on 2009-02-23
Someone correct me here if I'm wrong,,but if you are doing your update as soon as your install and thats it,,there should be a couple different programs you could use to make an image and burn it to a cd when finished of the update. I did this before when I finally had my system setup the way i wanted.

---

### Post by ikisham on 2009-02-23
To back-up your system for reinstall: [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by konqueror7 on 2009-02-23
try [APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by WatchingThePain on 2009-02-23
Or Incremental backups or is it differential (I can never remember) one of them resets the archive bit.Disc Images sound good..hopefully you can test them before saving as in the past I had some images that didn't work after the re-install.

---

### Post by dimitriv on 2009-02-24
APTonCD looks great, one small problem, i don't have a cd or dvd-rw (new machine coming soon...), can you create repository on local disk or external USB?

i'll also look at remastersys

thanks for the comments

---

### Post by egalvan on 2009-02-24
If you want to repeat the actual install, for instance you want the experience or to make changes, then...

Synaptic allows you to keep all downloads in a temporary cache.

Save and restore this cache, this should save you time.

If you don't want to repeat the actual install, then...
one of the backup options others talked about will be faster.

---

### Post by argie on 2009-02-24
If you want to just store all the packages that you have installed, they will be in /var/cache/apt/archives/. If you copy everything there to an external drive, and then copy back whenever you want to reinstall those programs, Synaptic will use those packages unless newer ones exist in the repository.

However, there's another way that I personally am a fan of. Use partimage to create an image of your / partition. Then restore from the partition every time you want a new installation.

---

### Post by philinux on 2009-02-24
Just reinstalled intrepid last night. Did all updates plus install ubuntu-restricted-extras, the medibuntu stuff, etc etc.

Now /var/cache/apt/archives is 490meg. Worth backing up if bandwidth or download limits are a problem.

---

### Post by geirha on 2009-02-24
> **dimitriv said:**
> APTonCD looks great, one small problem, i don't have a cd or dvd-rw (new machine coming soon...), can you create repository on local disk or external USB?

i'll also look at remastersys

thanks for the comments

APTonCD will create a CD/DVD-image, then it will ask you if you want to burn it as well. You can choose not to burn it, then just copy/move the iso-image to and usb drive or wherever you like.

To get the packages from the CD, you can:
1. extract the files from the .iso image as you would a .zip or .tar.gz file (right click it and open it with the archive manager), 
2. mount the iso-image with a command like ```
sudo mount -o loop /media/disk/aptoncd-20090224-CD1.iso /media/cdrom
```
3. install aptoncd on your new system, then use its restore feature which accepts an iso-image.

Either way, you just tell synaptic where you extracted the files or mounted the iso etc, and it will use them when you choose to install the applications you previously had. You can also just open a terminal, cd to the Packages directory and run ```
sudo dpkg -i *.deb
``` to install all the packages contained in the iso.

---

