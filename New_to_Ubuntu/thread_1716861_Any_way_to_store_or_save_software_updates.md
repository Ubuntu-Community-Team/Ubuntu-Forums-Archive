---
title: "Any way to store or save software updates?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-29
Hi,

Is there any way to download updates and store them somewhere so that they can be used on more than one machine?

Like if I install Linux on one computer, update it, then install Linux on another computer, is there a way to save downloading all 310MB of updates to the second computer?

---

### Post by plucky on 2011-03-29
> **Learning Linux 2011 said:**
> Hi,

Is there any way to download updates and store them somewhere so that they can be used on more than one machine?

Like if I install Linux on one computer, update it, then install Linux on another computer, is there a way to save downloading all 310MB of updates to the second computer?

The .deb files are in **/var/cache/apt/archives** and can be copied between machines.

Also look at a program called AptonCD which will create an .iso file with all the files in /var/cache/apt/archives location.You can then use the .iso file to transfer the files.

Good Luck

---

### Post by kevinamadeus2 on 2011-03-29
Exactly as plucky said.
Just copy the debs to the same directory on the new machine, and run ```
sudo apt-get update && sudo apt-get upgrade
``` or install any specific software. It will detect if the deb is there or it needs to be downloaded.

But please note that most debs saved are suitable only for that specific version of Ubuntu and whether it is 32bit or 64bit.

Extra: you can use ```
sudo apt-get autoclean
``` to erase the deb files that are old/not used in the archives folder, so you can save some space and backup time.

---

