---
title: "adobe flash player not working"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by brijraj22 on 2009-04-03
i have ubuntu 8.04 loaded on a pen drive from which i have booted. i tried to load the adobe flash player for running youtube videos but on downloading the package and opening it, the package manager is giving an error message "Error : Dependency is not satisfiable: libpango 1.0-0". can someone help me plz

---

### Post by James_Lochhead on 2009-04-03
Have you tried downloading the lib from the package manager first?

---

### Post by Cresho on 2009-04-03
System->administration->synaptic package manager

search for flash

tick "adobe-flashplugin"
hit apply.

make sure your browser is not running.

---

### Post by brijraj22 on 2009-04-03
tried it, but firefox is still not running flash contents.

---

### Post by SunnyRabbiera on 2009-04-03
are you using a 64bit system?

---

### Post by brijraj22 on 2009-04-03
no, i have core 2 duo processor, but the ubuntu loaded is 32 bit

---

### Post by philinux on 2009-04-03
Not sure if this will help or not.

[http://ubuntuforums.org/showthread.php?t=1044980](http://ubuntuforums.org/showthread.php?t=1044980)

---

### Post by gandaran on 2009-04-03
> **brijraj22 said:**
> i have ubuntu 8.04 loaded on a pen drive from which i have booted. i tried to load the adobe flash player for running youtube videos but on downloading the package and opening it, the package manager is giving an error message "Error : Dependency is not satisfiable: libpango 1.0-0". can someone help me plz
you have to install all system updates first only then you can install the package without getting any errors.

---

### Post by brijraj22 on 2009-04-05
i tried everything, removed the flash plugin-non free, installed it again by the synaptic manager, when it didn't work, i installed the swflash and then removed it again when it didn't work,i downloaded the tar.gz package from the adobe website and tried pasting the .so file in usr/lib/mozilla/plugins but cudnt do so coz i need root permission (havent been able to figure out a way past it till now but i'm trying). i've seriously gone nuts trying to install this flash player. 
is it because of any particular update that i have to load, coz im running the ubuntu on a pendrive and i dont want to fill up the remaining space on the pendrive with updates (dont have much space!!). someone plz help me

---

### Post by gandaran on 2009-04-05
> **brijraj22 said:**
> i tried everything, removed the flash plugin-non free, installed it again by the synaptic manager, when it didn't work, i installed the swflash and then removed it again when it didn't work,i downloaded the tar.gz package from the adobe website and tried pasting the .so file in usr/lib/mozilla/plugins but cudnt do so coz i need root permission (havent been able to figure out a way past it till now but i'm trying). i've seriously gone nuts trying to install this flash player. 
is it because of any particular update that i have to load, coz im running the ubuntu on a pendrive and i dont want to fill up the remaining space on the pendrive with updates (dont have much space!!). someone plz help me
open terminal and type **gksudo nautilus**, now you can paste that flashplugin (libflashplayer.so) file to /usr/lib/mozilla/plugins with the root nautilus window.
this will be the only way to have flash working if you don't want to update, the updates are necessary as there have been many system changes since 8.04 release and the .deb flash packages target different system installation folder.

edit; 
if gksudo nautilus doesn't work with pen-drive ubuntu try **sudo -i nautilus**

---

### Post by brijraj22 on 2009-04-05
brij@brij-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4550): WARNING **: Unable to add monitor: Operation not supported

this is what im getting.

---

### Post by gandaran on 2009-04-05
> **brijraj22 said:**
> brij@brij-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4550): WARNING **: Unable to add monitor: Operation not supported

this is what im getting.
maybe gksudo won't work with pen-drive ubuntu try **sudo -i nautilus**, if it still wont work I'll show how to use the command line move command

---

### Post by thesuperjman on 2009-04-05
i have ubuntu 8.10 and i downloaded adobe flash player but idk if it was the right one. i downloaded from here- [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and selected .deb for ubuntu 8.04+.  was this right? is there another way i shouldve downloaded.

---

### Post by gandaran on 2009-04-05
> **thesuperjman said:**
> i have ubuntu 8.10 and i downloaded adobe flash player but idk if it was the right one. i downloaded from here- [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and selected .deb for ubuntu 8.04+.  was this right? is there another way i shouldve downloaded. 
if it installs and works what more do you want?
there are many ways to install flash in linux, it doesn't matter which package you install so long it works.

---

### Post by thesuperjman on 2009-04-05
o sorry, i should've mentioned it doesnt work.

---

### Post by EnglishSparrow on 2009-04-05
Try a different browser like Konqueror or Seamonkey.

---

### Post by gandaran on 2009-04-05
> **thesuperjman said:**
> o sorry, i should've mentioned it doesnt work.
have you installed all updates? it won't work if you don't do it, if you don't want to update then install flash manually from the adobe tar.gz package.

---

### Post by digbickman on 2009-05-15
FROM ANOTHER THREAD:[http://www.uluga.ubuntuforums.org/showthread.php?t=894874&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=894874&page=2)
> **digbickman said:**
> Ok my system says it is up to date and did sudo apt-get update

This time when i installed flushplugin-nonfree i clicked details and noticed it says "download fail" at the end

Any clues?

Thanks
  

I then download adobe .deb for  hardy 8.04+

i get status: Dependency is not satisfiable: libpango 1.0-0

---

### Post by dondrup on 2009-05-21
hi there,
i am giving ubuntu a try again. this time i find the "sleep" function works, that was the last straw with 8.10 for me - i just couldn't get it to sleep or hibernate.

anyway my flash problem with 9.04 installed via wubi is that when i try to install the latest from the flash download page nothing happens. here is the terminal text after i've downloaded the latest .rpm:

sman@ubuntu:~$ /home/sman/Desktop/
bash: /home/sman/Desktop/: is a directory
sman@ubuntu:~$ # rpm -Uvh <rpm_package_file>
sman@ubuntu:~$

it just does nothing after the last line. same thing happens with the tar.gz

here are the instructions from the adobe installation instructions page. is ther something i am doing wrong or is the latest adobe flash not yet optimized for jaunty?:

Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Installation instructions for .rpm

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .rpm file to your desktop and wait for the file to download completely.
       3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user). The installer will instruct you to shut down your browser(s).
       4. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by dondrup on 2009-05-22
to answer my own question for anyone else with this problem:

when i tried to install via the .deb i got an error saying "wrong architecture i386" which apparently means i have a 64bit version installed [this is the default one with wubi!]. so seeing in other threads that it is a headache getting 32bit programs to work on 64 i decided to reinstall using the 32 bit. flash works perfectly now - installed using the .deb on the adobe site.

---

