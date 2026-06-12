---
title: "joy2key"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by now0pen on 2011-03-01
I installed this software through the ubuntu software center. It was installed, but it's not in the list of installed software. Where do I find it and how do I activate it?

[IMG]http://img233.imageshack.us/img233/2330/screenshotubuntusoftwar.png[/IMG]

I am going to use my logitech precision gamepad to play games. I've been using this on windows vista together with joy2key for some time now.

[IMG]http://www.itreviews.co.uk/graphics/normal/hardware/h683a.jpg[/IMG]

thanks!

---

### Post by howefield on 2011-03-01
It may well be a command line application ?

Try typing joy2key into a terminal and/or post at the joy2key forums

[http://sourceforge.net/projects/joy2key/forums/forum/822705](http://sourceforge.net/projects/joy2key/forums/forum/822705)

---

### Post by now0pen on 2011-03-04
I went to the sourceforge fork for joy2key, but couldn't find anything there. I made a few more searches on the ubuntu forum and found this-- 

[http://ubuntuforums.org/showpost.php?p=8265397&postcount=5](http://ubuntuforums.org/showpost.php?p=8265397&postcount=5)

Following the instructions, I was able to finish the first step, but on the second step, I got an error message--

```
jimsyyap@jimsyyap-desktop:~$ sudo apt-get install build-essential checkinstall
[sudo] password for jimsyyap: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-28-generi
   linux-headers-2.6.32-28
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot
  libtimedate-perl xz-utils
Suggested packages:
  debian-keyring
  debian-maintainers
The following NEW packages will be installed:
  build-essential checkinstall
  dpkg-dev fakeroot
  libtimedate-perl xz-utils
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,172kB of archives.
After this operation, 3,924kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid/main libtimedate-perl 1.1900-1 [41.4kB]
Get:2 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]
Get:3 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.5 [654kB]
Get:4 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:5 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid/universe checkinstall 1.6.1-10 [124kB]
Get:6 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]
Fetched 1,172kB in 29s (39.1kB/s)
Selecting previously deselected package libtimedate-perl.
(Reading database ... 176895 files and directories currently installed.)
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1900-1_all.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Selecting previously deselected package checkinstall.
Unpacking checkinstall (from .../checkinstall_1.6.1-10_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.1900-1) ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up build-essential (11.4build1) ...
Setting up checkinstall (1.6.1-10) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

jimsyyap@jimsyyap-desktop:~$ sudo apt-get build dep joy2keyE: Invalid operation build
jimsyyap@jimsyyap-desktop:~$ sudo apt-get build dep joy2key
E: Invalid operation build
jimsyyap@jimsyyap-desktop:~$ 

```What do I do next?

Thanks!

- total noob--first week on ubuntu.

---

### Post by andlinux on 2011-03-05
Why are you installing joy2key again ???

Like howefield said, open a terminal/console and type: joy2key 

I get this but there's no gamepad connected to my laptop.

```
~$joy2key
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.3   Binary built on Dec 22 2009 at 13:45:44

Error opening /dev/input/js0!
Are you sure you have joystick support in your kernel?

```

---

### Post by now0pen on 2011-03-08
I typed in joy2key on terminal and here's what I got:

```
jimsyyap@jimsyyap-desktop:~$ joy2key
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.3   Binary built on Dec 22 2009 at 10:44:26

Must specify a target!
jimsyyap@jimsyyap-desktop:~$ 

```I would like to use my logitech gamepad to play games on ubuntu. 

I've been looking into how to install joy2key on ubuntu but find myself facing a wall most of the time. I am looking into the possibility of installing joy2key inside wine and see how that works.

Thanks!

---

### Post by andlinux on 2011-03-09
Like the output is telling you, you need to specify a target.

Read this topic, this will help you. [http://ubuntuforums.org/showthread.php?t=646564&highlight=joy2key](http://ubuntuforums.org/showthread.php?t=646564&highlight=joy2key)

---

### Post by now0pen on 2011-06-29
for closure--I never did get around to figuring out how to use joy2key. Instead, I found and installed qjoypad from [here]("http://www.playdeb.net/install/qjoypad/4.1.0-1%7Egetdeb1"). QJoypad even has a gui making it easy to configure everything.

To install, simply follow the instructions on the top of the page. Soon as it is installed, I found it under Applications > QJoyPad. Clicking that, it automatically sits in my system tray. Configuring the keys was easy. I simply clicked on Quick Set. A small window appears asking me to click on a button or axis on the gamepad, then click on the corresponding button on my keyboard.

---

