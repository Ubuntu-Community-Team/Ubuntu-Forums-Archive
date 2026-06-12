---
title: "Please help... The sound system of my dell vostro 1015 is not working!!! :("
date: 2011-07-18
forum: New to Ubuntu
---

### Post by Newbie_M on 2011-07-18
[FONT=Verdana]I am new to Linux, I have installed Ubuntu 10.10 in my Dell Vostro 1015. 

My speaker, headphone and Internal speaker was working fine, till the time I searched the net and experimented without being sure.

The internal mice and the mice of headphone was not working, I searched the net and did the following.

In the terminal :
$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21 was shown.

then i executed the following commands:

sudo /sbin/alsa-utisudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-devls stop


cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2)

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils

After this I checked 
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23. 

Compilation information wass not shown.

then, I checked :
sudo alsaconf

It showed : No supported PnP or PCI card found.    
          &#9474;  Would you like to probe legacy ISA sound cards/chips?
I selected Yes
this took me to the next page asking :
                                             &#9474; 
               &#9474;    Probing legacy ISA cards might make        
 
               &#9474;    your system unstable.
I selected OK

after this, I restarted, the machine...

Till then, the Internal Speaker, Speaker and Headphone stopped working!!! The mice is not working either...

Pls pls pls help me... I am fearing, if I have unknowingly made some unrepairable mistake...









[/FONT]

---

### Post by Elfy on 2011-07-18
Thread moved to Absolute Beginner Talk from Tutorials.

---

### Post by Newbie_M on 2011-07-18
Somebody please help me... what command should I run, so that the laptop will work properly...:confused:

---

