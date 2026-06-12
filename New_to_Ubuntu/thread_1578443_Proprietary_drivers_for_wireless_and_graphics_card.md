---
title: "Proprietary drivers for wireless and graphics card"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by NDIS Wrapper on 2010-09-20
Hello,

I'm a total noob for Ubuntu (and I mean it).

I have recently installed Lucid Lynx on my 64 bit Dell laptop. When I   ran the Live CD before installing (just to try Ubuntu for some time) it   asked me whenever I was in wifi network if I wanted to install the   proprietary drivers for wifi device. But the  same did not happen after I  installed Ubuntu on HDD. So now I cannot  access internet from Ubuntu  interface. Why must this be happening ?
  
I read about the ndisgtk and tried to install it, but i could not find   it in package manager !!
What could be done ? If any pre- packages are to be downloaded can u plz   post the links here ?

Thanks

---

### Post by ibizatunes on 2010-09-20
Easy solution, (well maybe - finger crossed)
Get a ethernet cable plug it in to your router, and then download the drivers by clicking system > admin > hardware drivers
this may fix your problem easily without the use of commands line stuff
worth a try!!

---

### Post by 101011010010 on 2010-09-20
Hello.
Have you tried looking in Hardware Drivers?

> System/Administration/Hardware Drivers

---

### Post by NDIS Wrapper on 2010-09-21
> **ibizatunes said:**
> Easy solution, (well maybe - finger crossed)
Get a ethernet cable plug it in to your router, and then download the drivers by clicking system > admin > hardware drivers
this may fix your problem easily without the use of commands line stuff
worth a try!!


errr thats not possible. No ethernet cable connection here.. :(

---

### Post by NDIS Wrapper on 2010-09-21
> **101011010010 said:**
> Hello.
Have you tried looking in Hardware Drivers?

Yes. It didn't show anything untill i tried this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Now "Install Hardware Drivers" shows availability of wireless device but on clicking "activate" it it shows following error.

**SystemError: InstallArchives() failed**

Terminal output:
deep@deep-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture x86_64
Building initial module for 2.6.32-24-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
deep@deep-laptop:~$

---

### Post by DrMelon on 2010-09-21
That is because it is trying to connect to the internet to install the drivers. Put the Ubuntu CD in the drive and try it again - it should install them from the CD (like it did when it was in LiveCD mode)

---

### Post by Silent Warrior on 2010-09-21
Also make sure to install build-essential and module-assistant, or whatever that package is called these days. It looks to me like it can't find the command 'patch'. I don't have time to check it for you at the moment, but it'll either be directly in the package list, or part of something that will in all probability be pulled in as a dependency of build-essential.

---

### Post by NDIS Wrapper on 2010-09-21
> **DrMelon said:**
> That is because it is trying to connect to the internet to install the drivers. Put the Ubuntu CD in the drive and try it again - it should install them from the CD (like it did when it was in LiveCD mode)

Well, this is happening even when the Live CD is in the drive.

---

### Post by NDIS Wrapper on 2010-09-21
> **Silent Warrior said:**
> Also make sure to install build-essential and module-assistant, or whatever that package is called these days. 

Can you please give me more keywords. And this is through synaptic package manager i guess ??

---

### Post by bkratz on 2010-09-21
I believe posts 5 and 6 of this thread will give you the patch info
and location

[http://georgia.ubuntuforums.org/showthread.php?p=9517880](http://georgia.ubuntuforums.org/showthread.php?p=9517880)

---

### Post by beew on 2010-09-21
First of all, instead of using a live CD (which you cannot store anything and slow) You may want to use a live usb with persistence if your bios supports booting from usb (but there is an even better way, see below) I think live CD sucks and it takes a long time to do everything and I don't know why people still recommend live CD as the norm for installation and testing. 

Secondly, you can't install propietary graphic drivers in a live usb or a live CD because it doesn't support kernel updates or other changes that affect the whole system. Try to do system update and you will break it. With wifi drivers it is possible as long as you don't need to update the kernel in any way.

I think instead of using live CD or live usb you should make a full installation into an external drive (I have an installation on a 8 g flash drive for testing propietary drivers such as Nvidia drivers) and use that if you need to install propietary drivers.

P.S. It seems that you will need to install some kernel source packages and it may not work with a live system (usb or cd) as it may update the kernel. I could be wrong as I haven't tried that,--I always use full external installation for that kind of things,-- but it is definitely no go if you try to install graphic drivers in a live system.

---

### Post by beew on 2010-09-21
> **DrMelon said:**
> That is because it is trying to connect to the internet to install the drivers. Put the Ubuntu CD in the drive and try it again - it should install them from the CD (like it did when it was in LiveCD mode)

I don't think the live CD comes with proprietary drivers though.

---

### Post by bkratz on 2010-09-21
> **beew said:**
> I don't think the live CD comes with proprietary drivers though.



From the link he/she provided

b43/STA - No Internet access
If you do not have any other means of internet access on your computer, you will have to install bcmwl-kernel-source package from the restricted folder under ../pool/restricted/b/bcmwl on the Ubuntu install media. This may be done in the following manner depending on the installation media used:

So yes it can be done, it just expects the "patch" to be loaded first.

---

### Post by NDIS Wrapper on 2010-09-21
> **bkratz said:**
> I believe posts 5 and 6 of this thread will give you the patch info
and location

[http://georgia.ubuntuforums.org/showthread.php?p=9517880](http://georgia.ubuntuforums.org/showthread.php?p=9517880)


Can't install. Package installer gives this error in status:
Wrong Architecture 'i386'

So could it be some other version of patch package ?

---

### Post by NDIS Wrapper on 2010-09-21
> **beew said:**
> First of all, instead of using a live CD (which you cannot store anything and slow) You may want to use a live usb with persistence if your bios supports booting from usb (but there is an even better way, see below) I think live CD sucks and it takes a long time to do everything and I don't know why people still recommend live CD as the norm for installation and testing. 
Well, I used a live CD for installation. So are suggesting to reinstall from USB or something ?

> **beew said:**
> Secondly, you can't install propietary graphic drivers in a live usb or a live CD because it doesn't support kernel updates or other changes that affect the whole system. Try to do system update and you will break it. With wifi drivers it is possible as long as you don't need to update the kernel in any way.

Oh i c. So i guess that will even more complicated ! I'm still pondering why Ubuntu is better than Windows :D

> **beew said:**
> P.S. It seems that you will need to install some kernel source packages and it may not work with a live system (usb or cd) as it may update the kernel. I could be wrong as I haven't tried that,--I always use full external installation for that kind of things,-- but it is definitely no go if you try to install graphic drivers in a live system.

I would like to try this as well, as long as it doesn't strangle me mid-air. Which "kernel source package" did u mean ?

---

### Post by NDIS Wrapper on 2010-09-21
> **bkratz said:**
> From the link he/she provided

b43/STA - No Internet access
If you do not have any other means of internet access on your computer, you will have to install bcmwl-kernel-source package from the restricted folder under ../pool/restricted/b/bcmwl on the Ubuntu install media. This may be done in the following manner depending on the installation media used:

So yes it can be done, it just expects the "patch" to be loaded first.

Yes, it has to be included in CD as it worked fine while trying it from CD (w/o installation) (Well both wifi card as well as ATI graphics card)

So "patch".
How do I find the right version. The one in the last post by bkratz didn't work.

---

### Post by bkratz on 2010-09-21
sorry, I did not notice you were using 64 bits. It seems to be more difficult in 64 bits since the new versions of patch are for 2.6.33 kernel. anyway, I think you will find additional information here

[http://ubuntuforums.org/showthread.php?t=1468927](http://ubuntuforums.org/showthread.php?t=1468927)

Still looking for a better one.


Not really sure this one is appropriate either (some seems to be 32 bit some 64), but worth looking at anyway.

---

### Post by NDIS Wrapper on 2010-09-22
> **bkratz said:**
> sorry, I did not notice you were using 64 bits. It seems to be more difficult in 64 bits since the new versions of patch are for 2.6.33 kernel. anyway, I think you will find additional information here

[http://ubuntuforums.org/showthread.php?t=1468927](http://ubuntuforums.org/showthread.php?t=1468927)

Still looking for a better one.


Not really sure this one is appropriate either (some seems to be 32 bit some 64), but worth looking at anyway.



Here is the output. Instead of i386 though i downloaded amd64 coz as I remember the Live CD version read amd64 for 64 bit processors ! 

o/p:
deep@deep-laptop:~$ sudo dpkg -i patch*
[sudo] password for deep: 
dpkg: error processing patch* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 patch*
deep@deep-laptop:~$ sudo dpkg -i /media/win7/Users/Depp/Desktop/ubu temp/patch_2.6-2ubuntu1_amd64.deb
dpkg: error processing /media/win7/Users/Depp/Desktop/ubu (--install):
 cannot access archive: No such file or directory
dpkg: error processing temp/patch_2.6-2ubuntu1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /media/win7/Users/Depp/Desktop/ubu
 temp/patch_2.6-2ubuntu1_amd64.deb

tried twice (didn't know if patch* meant the location of file...)

---

### Post by bkratz on 2010-09-22
found this one, it seems to be pretty good, just make sure the .deb files are on your desktop when you do the
"
and from ~/Desktop/          (make sure you are in the correct directory-desktop)

sudo dpkg -i *.deb"

[http://ubuntuforums.org/showpost.php?p=9661529&postcount=4](http://ubuntuforums.org/showpost.php?p=9661529&postcount=4)

apparently the files needed are on the live cd.

---

### Post by NDIS Wrapper on 2010-09-22
> **bkratz said:**
> found this one, it seems to be pretty good, just make sure the .deb files are on your desktop when you do the
"
and from ~/Desktop/          (make sure you are in the correct directory-desktop)

sudo dpkg -i *.deb"

[http://ubuntuforums.org/showpost.php?p=9661529&postcount=4](http://ubuntuforums.org/showpost.php?p=9661529&postcount=4)

apparently the files needed are on the live cd.

Errr... i guess I need to know more about terminal commands.

This is what I got:

deep@deep-laptop:~$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
deep@deep-laptop:~$

And by Desktop u meant Ubuntu desktop right ? I tried substituting the Ubuntu desktop path in place of '*' in the said command. It didn't work either.

---

### Post by NDIS Wrapper on 2010-09-23
Please help me out here lest should I begin to feel ubuntu inferior to windows !

I'm sure u won't let that happen ! :)

---

### Post by NDIS Wrapper on 2010-09-23
> **bkratz said:**
> found this one, it seems to be pretty good, just make sure the .deb files are on your desktop when you do the
"
and from ~/Desktop/          (make sure you are in the correct directory-desktop)

sudo dpkg -i *.deb"

[http://ubuntuforums.org/showpost.php?p=9661529&postcount=4](http://ubuntuforums.org/showpost.php?p=9661529&postcount=4)

apparently the files needed are on the live cd.


Hey, finally I found out how to use this command from Desktop. I needed to change the directory by ~/Desktop/. This worked exactly the way the link said it would.

Now replying to the thread in Ubuntu. :) Thanks a lot for this. Half part done.

Now comes the graphics card issue !! I have ATI Readeon Graphics card...

---

### Post by NDIS Wrapper on 2010-09-23
Well, I checked the hardware "drivers" and now it does show the avaliablity for ATI/AMD Graphics card device.
But when tried to activate it gives me this :

[B]Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb) Unable to connect to in.archive.ubuntu.com:http:

[/B]What could be this ?

---

### Post by NDIS Wrapper on 2010-09-23
> **NDIS Wrapper said:**
> Well, I checked the hardware "drivers" and now it does show the avaliablity for ATI/AMD Graphics card device.
But when tried to activate it gives me this :

[B]Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb) Unable to connect to in.archive.ubuntu.com:http:

[/B]What could be this ?

I also tried downloading the package from the given link. And by same method as earlier from terminal, I'm getting this :

[B]deep@deep-laptop:~$ cd ~/Desktop/
deep@deep-laptop:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for deep: 
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 122430 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
 fglrx-amdcccle depends on libqtcore4 (>= 4:4.5.3); however:
  Package libqtcore4 is not installed.
 fglrx-amdcccle depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not installed.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-amdcccle[/B]



Any idea how to fix this ?

---

### Post by sandyd on 2010-09-23
> **NDIS Wrapper said:**
> Well, I checked the hardware "drivers" and now it does show the avaliablity for ATI/AMD Graphics card device.
But when tried to activate it gives me this :

[B]Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu5_amd64.deb) Unable to connect to in.archive.ubuntu.com:http:

[/B]What could be this ?
try changing system -> adminstration -> software sources.
change the server to "main server", and proceed with yes when it asks you if you wanna update 

oh, and theirs a fglrx bug with the current release of the kernel. 
to solve it, run the update manager, then install the driver from the Hardware Drivers window. It will fail. then do the instructions in my signature (where it says can't install ati drivers?) (note, it is important to let it fail, just to make sure that the kernel headers are downloaded)

---

### Post by NDIS Wrapper on 2010-09-25
Well it worked w/o doing anything !! 
As in I just followed the earlier half of what you said :

> **sandyd said:**
> try changing system -> adminstration -> software sources.
change the server to "main server", and proceed with yes when it asks you if you wanna update 
  



It worked just fine !!!
Thank you all very very much ! :)
Esp bkratz, sandyd, beew. Thank you.

---

### Post by bkratz on 2010-09-25
Glad to be of some small help, congratulations!

---

