---
title: "Trying to get sound to work on alienware m11x"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by qwiksilver711 on 2010-06-22
Hi, complete noob to linux, and ubuntu here.
I installed ubuntu 10.4 the wubi way on my alienware m11x, and am having trouble getting the sound to work. I found some drivers that should work with linux,  but being a complete noob I dont understand the readme on how to install, I'll paste the part of the readme that pertains to me below.

Installation:
This Source Code is from [www.alsa-project.org]("http://www.alsa-project.org").
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure --with-cards=hda-intel
    c. make
    d. make install

Step 3. reboot your machine

Step 4. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.6 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the [www.alsa-project.org]("http://www.alsa-project.org"), then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package. 



I pretty much done understand anything after step 1. I'm sorry for having to ask about such a mundane issue, and also I am sorry that I am that much of a noob. Normally I would just quit and go back to windows, but this OS is super sweet, and I feel like i'm at home on it, but just need to get the sound working before I really play with it more and actually make it a permanent thing. Thanks for the help guys.

---

### Post by phidia on 2010-06-22
The 1st step might be to open the terminal app and type > aplay -l copy and paste (or search) the output from that command. There is also available at the forums a sound troubleshooting guide-link [here]("http://ubuntuforums.org/showthread.php?t=205449"). It is a long thread but it can be helpful for sound issues.

---

### Post by lkjoel on 2010-06-22
Click on [Fix your Sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
Then check if your sound card is supported by OSS.
If so, then continue in the instructions.

---

