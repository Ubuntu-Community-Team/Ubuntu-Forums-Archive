---
title: "VirtualBox and USB drives"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by card_ace on 2009-02-18
i recently installed virtualbox on my ubuntu 8.10, hoping to run windows xp in it to make it easier to completely switch over.  my question is is there a way to make USB drives, or even my hard drive, appear inside of the virtualbox?

---

### Post by konqueror7 on 2009-02-18
you can share folders from your host to your guest os...

its in the settings...
```
net use x:\\vboxsvr\share
```
this should be inputted on your windows command line or run...

---

### Post by 73ckn797 on 2009-02-18
See if this thread will help you out:
[http://ubuntuforums.org/showthread.php?p=6090383](http://ubuntuforums.org/showthread.php?p=6090383)

---

### Post by Therion on 2009-02-18
Absolutely, but you need to install the PUEL (Personal Use/Evaluation License) version of VirtualBox.  The OSE (Open Source Edition) version of VirtualBox, that you get from the Ubuntu repository, does not have USB support *at all*.

---

### Post by lkraemer on 2009-02-18
card_ace,
Absolutley, but USB is NOT supported in the OSE version, so you will
have to go to [www.virtualbox.org](www.virtualbox.org) and download the version for your
distro.

Then there is a nice tutorial on the [www.pclinuxos.com](www.pclinuxos.com) website, in
the October 2008 issue of the PCLinuxOS Magazine.  You might want to
read through it.

lkraemer

---

### Post by card_ace on 2009-02-18
i'm not sure which version i have.  my ubuntu doesn't have internet access so what i've been doing is downloading updates through Keryx by creating a project and then downloading the updates on a windows machine with high speed.  so whichever version you get from keryx is the version i have, but to make sure i'll go to the virtualbox site and download it.  thanks for the tutorial too!

---

### Post by EXCiD3 on 2009-02-18
Just add the repository for Virtualbox to your sources.list in your Keryx project and download the latest package lists then you should be able to download "virtualbox-2.1" with Keryx which does support USB devices. :)

---

### Post by card_ace on 2009-02-19
i was wondering if someone could help me with windows xp.  i want to run it in virtualbox, and i got it installed, but i can't seem to find out how to access my shared folders.  in the tutorial that i downloaded in the issue of PCLinuxOS Magazine, it details how to access shared folders when running another linux version, but not how to access them on windows xp.

---

### Post by EXCiD3 on 2009-02-19
Use the Map Network Drive option in My Computer (in the Tools menu i think) and map your network shares as a drive such as the Z drive and you can easily access them.

---

### Post by lkraemer on 2009-02-20
You will also want to follow these directions on the [www.VirtualBox.org](www.VirtualBox.org) site

Note: Ubuntu users might want to install the dkms package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv and vboxnetflt) are properly updated if the linux kernel version changes during the next apt-get upgrade. 

Also, you will need to install the GuestAdditions.ISO, along with reading
the  information here:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
on Windows Shared Folders with a Windows GUEST VDI.

And don't forget the HOWTO's and TUTORIALS.

lkraemer

---

### Post by card_ace on 2009-02-20
> **EXCiD3 said:**
> Just add the repository for Virtualbox to your sources.list in your Keryx project and download the latest package lists then you should be able to download "virtualbox-2.1" with Keryx which does support USB devices. :)

i'm still kinda a linux noob so can you give me instructions on how to add the repository?

---

### Post by josecuervo86 on 2009-02-20
You can download the deb from here

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Virtual box HAD support for USB, you just have to make a simple change in the permissions file

In the console just put:
$ gksudo gedit /etc/udev/rules.d/40-permissions.rules

The change is this:

SUBSYSTEM==&#8221;usb_device&#8221;, MODE=&#8221;**0664**?

for this

SUBSYSTEM==&#8221;usb_device&#8221;, MODE=&#8221;**0666**?

Sorry for my english. I hope you understand it

---

### Post by EXCiD3 on 2009-02-20
Sure, open up your project folder in Keryx, go to the sources folder and open up sources.list and add this line:

```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```Actually now that I think about it, download the newest Keryx (which i released last night) from [http://keryxproject.org](http://keryxproject.org) and then create a project and use the Sources Editor in the Project menu of Keryx to add that line. Then all you need to do is select virtualbox-2.1 to download in Keryx. :D

---

### Post by card_ace on 2009-02-24
ok i got it up and running.  i added the repository in my ubuntu sources then created a keryx project, which allowed me to download it.  i installed it yesterday, along with the guest additions, and couldn't find my shared folders, but then i realized that i forgot to remake the shared folder in the new version of virtualbox.  duh. :)  thanks for the help!

---

### Post by EXCiD3 on 2009-02-24
Glad to see you got it working. VBox is awesome! :D

---

