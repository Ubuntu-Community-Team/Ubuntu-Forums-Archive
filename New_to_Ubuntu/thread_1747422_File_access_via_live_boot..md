---
title: "File access via live boot."
date: 2011-05-02
forum: New to Ubuntu
---

### Post by SapientShell on 2011-05-02
Hi! This is my first post so bare with me. 

Here's my question:

If I put my Ubuntu on a USB stick and start it up in live mode on another computer that runs windows (Windows 7 for example), would I be able to access the hard drives and manipulate the files on them?

---

### Post by DogMatix on 2011-05-02
Yes, it is possible. You should find your windows install in the places menu. But be careful you don't damage your Windows installation.

This may help although a little dated [LINK](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

---

### Post by SapientShell on 2011-05-03
Thanks for the reply! I figured it would be as simple as that but better safe than sorry :D

When you say that I might damage my windows installation what do you mean? Could the system be damaged by me simply moving/copying/erasing files, normal stuff like that? There's nothing terribly important on that computer but it does serve a purpose so I still want it functional!

---

### Post by I2k4 on 2011-05-03
If you're on windows and want to run from Live USB, these instructions are bullet proof - read the "Show Me How":

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The one thing left out is the "Persistence" option on the Pendrive installer.  My experience testing several versions is that Ubuntu needs something less than 1GB of USB drive space.  The rest of the available drive space should be set to "Persistence" for additional packages and to store settings.  

In testing from USB drives, every version of Ubuntu but one so far has recognized the hard drive and external drives in the File Manager.  The one exception was Xubuntu - it just wouldn't see my hard drive so I gave up on it.

I suggest using a 4GB USB thumb drive, but I'm running a minimal install on my netbook from a 2GB drive (with GIMP, Google Earth, Firefox, Chrome, DropBox, Abiword, FBReader, and the excellent GLChess and GnuBackgammon games) very nicely. 

There is no damage from using Live USB with Persistence - it's a great way to reality test Ubuntu and its spin offs, like Lubuntu.

My best advice is, 
1) don't try to do too much at one time with a USB drive.  Delete what you don't want and install what you want one or two applications at a time, instead of mass.
2) don't do general "updates" of a USB installation
3) wherever possible, set your applications to use the hard drive instead of the default USB drive for caches, swap files, or storage (this can be done with Firefox, GIMP, etc.)
 
all because the USB is so much slower than the hard drive.  

Finally, I've found that to minimize useless muck on a USB drive, set the Synaptic Package Manager to delete storage of downloads, and a "cleaner" application like Bleachbit is great.  Have fun.

---

