---
title: "can't install mplayer or codecs to my karmic"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by pak bear on 2010-03-29
hi to all ubuntu's gurus...i'm a total newbie to this application...i have a problems here...i can't install mplayer to my karmic even using the command...it always give me this

sudo apt-get install mplayer
reading package lists...done
building dependency tree
reading state information...done
E: Couldn't find package mplayer

please someone help me out here....:D

---

### Post by kleskjr on 2010-03-29
try with synaptic better, you can find it there
system > administration > synaptic package manager

---

### Post by pak bear on 2010-03-29
i'm sorry...i don't really get what u want me to do...

---

### Post by kleskjr on 2010-03-29
you should go to the main menu (usually it is on the top left), click on system, then administration and there you see synaptic package manager.

Other way to open synaptic is simply to write in the terminal:

sudo synaptic

and in quick search you can write the mplayer, thick it and then apply

Other way to find interesting software is to use Ubuntu software center (right there in the main menu)

have fun!

---

### Post by xifer on 2010-03-29
could be your sources list is not correct.

from the start menu, find synaptic package manager program or kpackage if you don't have synaptic. This is a GUI alternative to apt-get.

 Look in the menu options for software sources and ensure you have everything selected.  

Then look for the reload option - that will refresh the lists of available packages.  


Then try again with mplayer.

---

### Post by sisco311 on 2010-03-29
mplayer is in the multivers repository. Enable it: System > Administration > Software Sources.
[uhelp]community/Repositories/Ubuntu[/uhelp]

or run:
```
sudo software-properties-gtk -e multiverse
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by shindou01 on 2010-03-29
> **kleskjr said:**
> you should go to the main menu (usually it is on the top left), click on system, then administration and there you see synaptic package manager.

Other way to open synaptic is simply to write in the terminal:

sudo synaptic

and in quick search you can write the mplayer, thick it and then apply

Other way to find interesting software is to use Ubuntu software center (right there in the main menu)

have fun!

for a complete novice such as myself a couple of days ago, it would be easier if you use Ubuntu Software Center to install things...

try to find mplayer from Ubuntu Software Center (Applications->Ubuntu software center->Sound & Video)
if you can't find it or you found it but it won't install, try to update Ubuntu first (System->Administrations->Update Manager->check for updates, install updates and reboot if required) then try Ubuntu Software Center again...

good luck pak bear...(mr beruang??indonesian I assume??pm me if you are)

---

### Post by coffeecat on 2010-03-29
> **pak bear said:**
> 
E: Couldn't find package mplayer

That sounds as though you haven't refreshed your package metadata since you installed. Make sure you have an internet connection, and:

```
sudo apt-get update
```**Or**

Go to System > Administration > Synaptic and click on 'reload'.

---

### Post by pak bear on 2010-03-30
thank you all for your reply....i will try it :)

---

### Post by Amipagol on 2010-03-30
The best way of doing is go to [www.appnr.com](www.appnr.com) and find Gstream codec and install all of them. Then search for mplayer. You can click and install.

---

### Post by pak bear on 2010-03-30
sorry to bother u guys again...after i update it...and i wanted to install mplayer it gave me this error....

faridz@ubuntu:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaudio2 libavcodec52 libavformat52 libavutil49 libcelt0 libfaac0 libffado1
  libfreebob0 libgsm1 libjack0 liblzo2-2 libmp3lame0 libopenal1 libpostproc51
  libschroedinger-1.0-0 libsvga1 libswscale0 libx264-67 libxml++2.6-2
  libxvidcore4 mplayer-nogui mplayer-skins
Suggested packages:
  nas jackd mplayer-doc netselect fping nvidia-libvdpau1 nvidia-libvdpau
The following NEW packages will be installed:
  libaudio2 libavcodec52 libavformat52 libavutil49 libcelt0 libfaac0 libffado1
  libfreebob0 libgsm1 libjack0 liblzo2-2 libmp3lame0 libopenal1 libpostproc51
  libschroedinger-1.0-0 libsvga1 libswscale0 libx264-67 libxml++2.6-2
  libxvidcore4 mplayer mplayer-nogui mplayer-skins
0 upgraded, 23 newly installed, 0 to remove and 151 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

why?????

---

### Post by xifer on 2010-03-30
You can only run one installer at a time - either use the GUI (synaptic/kpackage/ubuntusoftwarecenter)  to do the install or close it before trying to use apt-get on the command line.

---

### Post by sisco311 on 2010-03-30
> **xifer said:**
> You can only run one installer at a time - either use the GUI (synaptic/kpackage/ubuntusoftwarecenter)  to do the install or close it before trying to use apt-get on the command line.

+1

@OP:
BTW, if you want to try a complete (GUI) front-end for MPlayer then try [SMplayer]("http://smplayer.sourceforge.net/"). It's in the repos:
```
sudo apt-get install smplayer
```

---

### Post by pak bear on 2010-03-30
thanks for your reply...the problem solved...i used apt-get command twice...hihi:P

---

### Post by sisco311 on 2010-03-30
> **pak bear said:**
> thanks for your reply...the problem solved...i used apt-get command twice...hihi:P

Cool!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

