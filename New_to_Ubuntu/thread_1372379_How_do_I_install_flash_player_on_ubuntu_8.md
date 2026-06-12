---
title: "How do I install flash player on ubuntu 8"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by antiwindowsman on 2010-01-04
Hi I have just started using Ubuntu Linux, My computer has a ASUS  a7n8x mutherbord with a x86 prossesor and Ubuntu 8 is the best it can handle.  I cannot get the flash player to install, Is this a lost cause or can i get it to work, If so ,How? Please help.

---

### Post by bobbob1016 on 2010-01-04
First off, it helps to specify the last two numbers too 8.xx, either .04 or .10.

Secondly, Adobe.com -> Get Flash Player -> Select Version To Download -> .deb Ubuntu 8.04+  [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

(edit) Second-and-a-half-ly, Double click the file you downloaded, enter your password, and click install, then restart FireFox.

Third, the motherboard doesn't (really) say what version you can run, the CPU/GPU/RAM do.  However, I've heard of 9.10 running on really old hardware, Pentium III's and lower are common.

---

### Post by antiwindowsman on 2010-01-04
Thanks., it is 8.04 and i had to upgrade it from 7.??, and Adobe does not have an option for 8.04 just 8.10, and i tryed it using both bash and sudo,  and i gave you the motherbord info thinking you might google it if you needed more info. 
  I am sorry i am vary new to the softwhare end of computers,

---

### Post by snowpine on 2010-01-04
I recommend opening a terminal (Applications->Accessories->Terminal) and:

```
sudo apt-get install flashplugin-nonfree
```

This will install the "correct" Flash that's been tested for your Ubuntu version. Good luck!

---

### Post by bobbob1016 on 2010-01-04
You are making it harder than it has to be, no bash needed here.  Go to that site in FireFox.  And I know for a fact that Adobe has one in the pull down menu titled ".deb for Ubuntu 8.04+" because I am looking right at it.

[IMG]http://imagebin.ca/view/VZhQgP.html[/IMG]
[http://imagebin.ca/view/VZhQgP.html](http://imagebin.ca/view/VZhQgP.html)

If that doesn't work, do:
System -> Administration -> Synaptic Package Manager
Then search for "flash" and click install, then restart FireFox.

Edit:  Thanks snowpine, didn't remember the exact way on 8.xx, and I thought sticking with GUI would be better, didn't know if flash was in 8.xx's repos either.

---

### Post by antiwindowsman on 2010-01-04
Thanks for the help but all i get is "dependncy is not satisfiable:libpango 1.0=0 , it is a amd athlon not a k64 , my mistake, but still no go.

---

### Post by antiwindowsman on 2010-01-04
huey@Swamp:~$ sudo updatedb
[sudo] password for huey: 
huey@Swamp:~$ sudo updatedb
huey@Swamp:~$ locate libflash
/home/huey/.local/share/Trash/files/libflashplayer (copy).so
/home/huey/.local/share/Trash/files/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
/home/huey/.local/share/Trash/files/libflashplayer.2.so
/home/huey/.local/share/Trash/files/libflashplayer.3.so
/home/huey/.local/share/Trash/files/libflashplayer.so
/home/huey/.local/share/Trash/info/libflashplayer (copy).so.trashinfo
/home/huey/.local/share/Trash/info/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz.trashinfo
/home/huey/.local/share/Trash/info/libflashplayer.2.so.trashinfo
/home/huey/.local/share/Trash/info/libflashplayer.3.so.trashinfo
/home/huey/.local/share/Trash/info/libflashplayer.so.trashinfo
/home/huey/Desktop/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
huey@Swamp:~$ uname -m
i686
huey@Swamp:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
huey@Swamp:~$ dpkg -s flashplugin-nonfree
Package `flashplugin-nonfree' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
huey@Swamp:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
huey@Swamp:~$ dpkg -s swfdec-mozilla
  
  Maby this info will help us figure it out. and Thanks for your help,,all of you.

---

### Post by steveneddy on 2010-01-04
Looks like you have a copy of libflashplayer.so on your desktop - yes?

in terminal

```
cd ~/Desktop
```

then

```
cp libflashplayer.so /usr/lib/mozilla/plugins
```

then

```
ls
```

to list plugins in that file, just to make sure that it is there, then simply restart Firefox and go to a Flash site to see if it works.

I recommend that you copy and paste these commands in your terminal instead of typing them out.

Good luck

---

### Post by antiwindowsman on 2010-01-04
I have tryed everything this is my term window. I can't understand why it cant see the file.

 huey@Swamp:~/Desktop$ cp flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64 /usr/lib/mozilla/plugins
cp: cannot stat `flashplugin-nonfree_9.0.31.1.4ubuntu2_amd64': No such file or directory
huey@Swamp:~/Desktop$ ls
AdbeRdr9.2-1_i486linux_enu.bin
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64.deb
gcalctool.desktop
install_flash_player_10_linux(2).deb
install_flash_player_10_linux(3).deb
install_flash_player_10_linux.deb
install_flash_player_10_linux.tar.gz
libflashplayer.so
redhat-manage-print-jobs.desktop
huey@Swamp:~/Desktop$

---

### Post by antiwindowsman on 2010-01-04
Now it says this,,,, i changed a 1 to a 0 is all, makes a big differance,  i think it did it .

  huey@Swamp:~$ cd ~/Desktop
huey@Swamp:~/Desktop$ cp flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64 /usr/lib/mozilla/plugins
cp: omitting directory `flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64'
huey@Swamp:~/Desktop$ ls
AdbeRdr9.2-1_i486linux_enu.bin
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64.deb
gcalctool.desktop
install_flash_player_10_linux(2).deb
install_flash_player_10_linux(3).deb
install_flash_player_10_linux.deb
install_flash_player_10_linux.tar.gz
libflashplayer.so
redhat-manage-print-jobs.desktop
huey@Swamp:~/Desktop$

---

### Post by antiwindowsman on 2010-01-04
now it says   
  
  huey@Swamp:~$ cd ~/Desktop
huey@Swamp:~/Desktop$ ls
AdbeRdr9.2-1_i486linux_enu.bin
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64
flashplugin-nonfree_9.0.31.0.4ubuntu2_amd64.deb
gcalctool.desktop
install_flash_player_10_linux(2).deb
install_flash_player_10_linux(3).deb
install_flash_player_10_linux.deb
install_flash_player_10_linux.tar.gz
libflashplayer.so
redhat-manage-print-jobs.desktop
huey@Swamp:~/Desktop$ cp libflashplayer.so /usr/lib/mozilla/plugins
cp: cannot create regular file `/usr/lib/mozilla/plugins/libflashplayer.so': Permission denied
huey@Swamp:~/Desktop$

---

### Post by adam814 on 2010-01-04
All you're missing now is that you need to use sudo.  The /usr directory is owned by root and your normal user doesn't have permission to write to it.
```
sudo cp libflashplayer.so /usr/lib//mozilla/plugins/
```Then restart firefox and type about:plugins in the location bar to make sure you have a flash plugin installed.

---

### Post by LuisGMarine on 2010-01-04
Run this in a terminal window and post back the output.

```
uname -a
```

---

### Post by Methuselah on 2010-01-04
> **snowpine said:**
> I recommend opening a terminal (Applications->Accessories->Terminal) and:

```
sudo apt-get install flashplugin-nonfree
```

This will install the "correct" Flash that's been tested for your Ubuntu version. Good luck!

What happened when you did the above?

---

### Post by antiwindowsman on 2010-01-04
This....
  
  huey@Swamp:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for huey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
huey@Swamp:~$

---

### Post by snowpine on 2010-01-04
> **antiwindowsman said:**
> This....
  
  huey@Swamp:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for huey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
huey@Swamp:~$

Ooops... sorry, can you try:

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

?

(but only do this if you're not following the download-from-the-Adobe-site method; you're getting 2 conflicting suggestions here, so you need to pick one and follow it!)

---

### Post by antiwindowsman on 2010-01-04
It updated, so sudo works but this is what happened.

  huey@Swamp:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
huey@Swamp:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
huey@Swamp:~$ 
  

Ohh and Thanks

---

### Post by plucky on 2010-01-04
> **antiwindowsman said:**
> It updated, so sudo works but this is what happened.

  huey@Swamp:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
huey@Swamp:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
huey@Swamp:~$ 
  

Ohh and Thanks

You only have the main repository enabled.To install flash plugin in Hardy,you have to have the Multiverse repository enabled.

Go to **System > Administration > Software Sources** and make sure the first four boxes are ticked.(See screenshot)

Then run ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```


Good Luck

---

### Post by antiwindowsman on 2010-01-04
This worked,,,,,SOLved!!! Thank you, it only took us 11 hours to figure out i needed to check some box's to make it work.

---

