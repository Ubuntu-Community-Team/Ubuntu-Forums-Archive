---
title: "Nvidia 256.35 and 256.44 Major problem"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by phazixc on 2010-08-04
I'm Running:-

Toshiba q505 888

Ubuntu 10.04 lucid 64Bit

Core 7i q740
Nvidia Gts 360m 1gb
4 Gb Ram 


I Updated to 256.35 = Excellent / perfect

Then my updates from X-swat and Xorg Egders updated to 256.44 this = my world falling apart.

My system completely locks up / hags / kills its self within 4 mins of logging in. 

If I load anything I.E wine to run a game. 

It really doesnt like that... My problem is i'm only a year into ubuntu and I have done manual updates before, but what im doing isnt working as I have tried purge remove nvidia .44 and disabling the two ppa's then manually installing .35 ..

BUT

when I start the gdm = great it works, then when I restart = not great....because I'm on failsafe graphics and the x sever setting not in menu (if it is in menu then theres nothing in there; apart from that msg to restart X) and when I load Hardware drivers the nvidia card isnt there..

I would like to think that some of your reading this are laughing because you are what I would call a pro in the ubuntu area and that you could / will post a detailed step by step to help me install .35 through the x-swat or x-org egder ppa or even manually download it and install it that way, so when I restart it works, and more to the point I can keep those two ppa's in my system so when i hit the update button I can see ubuntu wants to update to .44 which I WONT DO....

One year into ubuntu and I haven't logged into windows since.

As I find theres always someone will to help fix something in ubuntu..

anyway thats that, Mr/Mrs pro.... can you post that guide please.

P.S im currently on Linux-x86_64 NVIDIA Driver Version: 195.36.24 Server Version Number: 11.0 and Server Vendor Version: 1.8.2 NV-CONTROL Version: 1.22
gnome 2.30.2 and kernel linux 2.6.32-24 generic
platform X86_64



Thanks

---

### Post by MCunha on 2010-08-05
Hi,
 
See if you still have the downloaded packages from 256.35. It is keeped in:
 
/var/cache/apt/archives/
 
If you do have it, is easy: remove your current drivers. Using a text console, type (not sure if these are the packages from your current instalation):
 
```
sudo apt-get purge nvidia-glx-195 nvidia-glx-195-dev nvidia-195-kernel-source
```
 
Then reinstall the 256.35. Open a console and type (replace the packages for the ones you've found, since I'm running karmic):
 
```
cd /var/cache/apt/archives/
sudo dpkg -i nvidia-256-kernel-source_256.35-0ubuntu1~karmic~nvidiavdpauppa3_i386.deb nvidia-glx-256_256.35-0ubuntu1~karmic~nvidiavdpauppa3_i386.deb nvidia-glx-256-dev_256.35-0ubuntu1~karmic~nvidiavdpauppa3_i386.deb
```
 
Cheers.

---

### Post by phazixc on 2010-08-16
excellent thanks

---

