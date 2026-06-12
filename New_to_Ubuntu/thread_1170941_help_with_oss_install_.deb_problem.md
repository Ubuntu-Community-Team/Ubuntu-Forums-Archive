---
title: "help with oss install .deb problem"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by PLANETARY on 2009-05-26
I got a new sweet sound card. I hear that OSS is better than alsa so that is why i am installing it. I am hung up in the actual install of the package. asla is off and I switched to oss but it gives me a problem with depackaging. I downloaded the 4.1 on my desktop and get this.

```
sudo dpkg -i oss-linux*.deb 
dpkg: error processing oss-linux*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux*.deb

```

I tried the tar and rpm file too with no luck, they are confusing to me.

soundcard is an Auzentech x-plosion cinema 7.1

P3 tualatin - Asus tusl2-c - 512ram - geforce fx5500 soon to have 6200 

Thanks

---

### Post by benerivo on 2009-05-26
Where did you download the .deb file from? Did you reach it via the [ubuntu wiki page]("https://help.ubuntu.com/community/OpenSound")? If you haven't tried this already, then download the deb file linked on that wiki page and using the actual file name, do```
sudo gdebi /home/ben/Desktop/theossdebfile.deb
```

---

### Post by PLANETARY on 2009-05-26
I DL it from 4front's website (oss)

I still don't get anywhere, the gdebi says the same thing. the install guide says that gdebi doesn't like it

```
root@Tualatin:~# sudo gdebi /home/alex/Desktop/oss-linux-4.1-1052_i386.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

```

also when i try to convert teh rpm file using alien I get

```
root@Tualatin:~# cd ~/desktop
bash: cd: /home/alex/desktop: No such file or directory

```

I usually get the 'no such file or dir' message it is discouraging. Am I doing something wrong? I dont understand

Thanks

---

### Post by kerry_s on 2009-05-26
misunderstanding

---

### Post by PLANETARY on 2009-05-26
I did that command kerry and it did a bunch of stuff then i rebooted now it doesn't seem to be installed. osstest ossxmix don't do anything.

---

### Post by kerry_s on 2009-05-26
misunderstanding

---

### Post by benerivo on 2009-05-27
> **PLANETARY said:**
> ...also when i try to convert teh rpm file using alien I get

```
root@Tualatin:~# cd ~/desktop
bash: cd: /home/alex/desktop: No such file or directory

```

I usually get the 'no such file or dir' message it is discouraging. Am I doing something wrong? I dont understand

Thanks

Follow the wiki guide, but make sure you are in the right folder before running the dpkg -i command. Put the .deb file on the Desktop and do```
cd ~/Desktop
```Although OSS 3 is old, the wiki refers to OSS 4 which is alive and current.

---

### Post by Gen2ly on 2009-05-27
Yeah, OSS rocks - great sound system.  Don't listen to planetary, he's talking about the old version of oss and the libraries he told you to install are for alsa compatibility with oss.  I'd ask the front4 guys why the deb package isn't installing, probably an error in making it.  Just played Quake Wars, Prey with OSS installed and it runs good.

---

### Post by kerry_s on 2009-05-27
> **benerivo said:**
> Follow the wiki guide, but make sure you are in the right folder before running the dpkg -i command. Put the .deb file on the Desktop and do```
cd ~/Desktop
```Although OSS 3 is old, the wiki refers to OSS 4 which is alive and current.

oh, i see what you guys are following, i missed your link up there.
i'll let you guys take care, as i never used that oss before.

---

### Post by PLANETARY on 2009-05-28
ok I got a response from 4front, I was referred to [http://www.4front-tech.com/forum/viewtopic.php?t=1438]("http://www.4front-tech.com/forum/viewtopic.php?t=1438") I did the steps with no luck, am I doing something wrong? I even did cd /usr/src/linux-headers-`uname -r`/ that was recommended below the first post. 


```
alex@Tualatin:~$ sudo bash
root@Tualatin:~# sudo apt-get install gcc 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgda3-common python-gnome2-extras
  libgdl-gnome-1-0 libgda3-3 linux-headers-2.6.24-19 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
root@Tualatin:~# sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
make is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgda3-common python-gnome2-extras
  libgdl-gnome-1-0 libgda3-3 linux-headers-2.6.24-19 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
root@Tualatin:~# sudo apt-get install binutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgda3-common python-gnome2-extras
  libgdl-gnome-1-0 libgda3-3 linux-headers-2.6.24-19 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
root@Tualatin:~# sudo apt-get install linux-headers-`uname -r` 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-22-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgda3-common python-gnome2-extras
  libgdl-gnome-1-0 libgda3-3 linux-headers-2.6.24-19 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
root@Tualatin:~#  sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgda3-common python-gnome2-extras
  libgdl-gnome-1-0 libgda3-3 linux-headers-2.6.24-19 libgdl-1-0
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
root@Tualatin:~# cd /usr/src/linux-headers-`uname -r` 
root@Tualatin:/usr/src/linux-headers-2.6.24-22-generic# sudo make prepare 
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
root@Tualatin:/usr/src/linux-headers-2.6.24-22-generic# sudo make prepare scripts 
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
root@Tualatin:/usr/src/linux-headers-2.6.24-22-generic# sudo dpkg -i oss-linux*.deb 
dpkg: error processing oss-linux*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux*.deb
root@Tualatin:/usr/src/linux-headers-2.6.24-22-generic# 
```

---

### Post by achase79 on 2009-05-28
the problem is you are not pointing dpkg to the file correctly.  In terminal you could just type "sudo dpkg -i " then drag-n-drop the oss-linux*.deb file onto the terminal window.  This will place the correct path to the file into the command line.  Then all you have to do is click on the terminal window and press enter.

---

### Post by PLANETARY on 2009-05-28
oh wait! I got it, I did cd ~/Desktop then sudo dpkg -i oss-linux*.deb and it installed. I got the mixer up now and got analog channels to work however optical i cant get working yet.

thanks achase79 for telling me a can drag and drop that is quite helpful.

Thanks for help.

---

