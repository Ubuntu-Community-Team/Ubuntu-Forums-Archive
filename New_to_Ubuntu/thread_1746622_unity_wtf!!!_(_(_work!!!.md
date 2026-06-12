---
title: "unity wtf?!?!?!? :( :( work!!!"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by eddiimonster on 2011-05-02
ok so i have a Compaq Presario SR1230NX desktop. I installed 11.04 and its stating i can not support unity... it has integrated video, PLEASE tell me i can get it to work with this desktop.....

---

### Post by Kaladin72 on 2011-05-02
You can run Ubuntu in the Classic mode by selecting it in the drop down menu at the bottom of your screen at the log-in window.

---

### Post by eddiimonster on 2011-05-02
i have it in classic mode but im very much bored with it as of now... haha id REALLY love to have unity... i fell in love with it.

---

### Post by beew on 2011-05-02
> **Kaladin72 said:**
> You can run Ubuntu in the Classic mode by selecting it in the drop down menu at the bottom of your screen at the log-in window.

Shouldn't that be automatic if Op's hardware doesn't support Unity?

---

### Post by Kaladin72 on 2011-05-02
Yeah, I reckon so. Sorry. I'm quite ignorant regarding Ubuntu. I just knew that one solution.

---

### Post by eddiimonster on 2011-05-02
haha ya i personally dont like the look of it without unity, one of the main reasons i dropped openSUSE to come over to ubuntu... so im hoping someone can help me out!

---

### Post by kaldor on 2011-05-02
Well, first you can start by telling us which graphics card you have :)

---

### Post by wilee-nilee on 2011-05-02
Op confirm your graphics card I believe it is this EVGA nVidia GeForce 6200 
In the terminal.
lspci | grep VGA

Look in the menu-system-admin-additional drivers and see if there is one or any for loading.

---

### Post by uRock on 2011-05-02
> **wilee-nilee said:**
> look in the menu-system-admin-additional drivers and see if there is one or any for loading.

+1 :)

---

### Post by eddiimonster on 2011-05-02
I've already tried to load drivers and nothing will come up for them. And it is intergrated that came with the comp. 
mass@pwnage:~/Desktop$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
dont know if thats what you need, im super new to the linux thing. getting used to it still

---

### Post by Furyhunter on 2011-05-02
Have you checked to see if there are any Additional Drivers you can install? Your graphics card may need proprietary drivers that Ubuntu doesn't provide by default because you have to accept a license...

If all else fails, you can try the unity-2d project. It's an attempt to implement the Unity interface without desktop compositing and OpenGL. Run the following command in a terminal:
```
$ sudo apt-get install unity-2d
```

if you want to use the daily builds of the latest code do this instead,
```
$ sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
$ sudo apt-get update
$ sudo apt-get install unity-2d
```

Keep in mind that Ubuntu does not update packages beyond bug and security fixes at each release (for stability reasons), so in order to get bleeding edge packages, you need to use PPAs from Launchpad, other repositories or build directly from source.

---

### Post by beew on 2011-05-02
> **Furyhunter said:**
> Have you checked to see if there are any Additional Drivers you can install? Your graphics card may need proprietary drivers that Ubuntu doesn't provide by default because you have to accept a license...



The card seems really old, maybe the Nvidia driver has not been upgraded to Natty. 

In any case nouveau should be good enough for Unity if you install the package libg1-mesa-dri-experimental. I installed Natty on an external drive and use only nouveau so the installation is portable. I have been using full Unity on my Nvidia laptop since alpha (Nvidia G105M)

EDITED: Since this seems like a pre VDPAU card if nouveau works I wouldn't go through the troubles of installing the Nvidia driver since I read in the forum support for Natty maybe sketchy at this point,

---

### Post by clhsharky on 2011-05-02
eddiimonster

unity-2d is your best chance at Unity.
> VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
VIA Technologies S3 UniChrome chip has no 3D drivers for latest releases.
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)


Sharky

---

