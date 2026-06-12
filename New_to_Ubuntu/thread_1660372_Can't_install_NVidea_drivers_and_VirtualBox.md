---
title: "Can't install NVidea drivers and VirtualBox"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Japster on 2011-01-05
I'm very new with Linux and are in need of some assistance.

I'm using a NVidea Geforce graphics card and downloaded the drivers for linux. The things is I can't get it installed. It says it needs to be installed from the root. How do I do that???

Then I also downloaded VirtualBox3.1.8 for Linux and tried to install it. It is already compiled, it is just a single file with the .run extension at the back. When I want to install it, it says I need to have administrator rigts to install it, but I'm the only user on Linux and when I go and check Im a administrator. How do I get pass this mistake. I tried to use the suno command, but don't know how it really works and could not get it right. 

I;m using Ubuntu 9.10

Please any help will be appriciated

):P

---

### Post by Spyderkid on 2011-01-05
Just go to System > Administration and enable the recommended NVidea driver.
For Virtual box go to the software centre and download VirtualBox OSE

---

### Post by Zzl1xndd on 2011-01-05
If you go to System > Preferences > Hardware Drivers it may list the driver for you card. this is the easiest way to install these drivers. 

As for Virtual Box there should be an Ubuntu Specific version on the VB site that you can download just double click and it will start the process. Or click the link below to download it.

[http://download.virtualbox.org/virtualbox/4.0.0/virtualbox-4.0_4.0.0-69151~Ubuntu~karmic_i386.deb](http://download.virtualbox.org/virtualbox/4.0.0/virtualbox-4.0_4.0.0-69151~Ubuntu~karmic_i386.deb)

---

### Post by Japster on 2011-01-05
Thanks for the advice so far. 

I have downloaded the NVidea drivers on my xp pc. It is NVidea drivers for Linux. I then copied it to my Linux partition. When I start Ubuntu and want to install it, it gives my a window with 4 opions. Run in Terminal, 2 others and Run. When I click Run in terminal, it says it must be installed from the root. Now when I go to the hardware section, it doesn't show the drivers I download. Is there a specific folder I must copy it to. I'm really a newbie with linux and know nothing.

Coming to the VirtualBox, I also downloaded the installion file for Linux. But when I want to install it, it gives my that same dailog box with the 4 options. When I pick run in terminal, it says It can't be installed without administrator priviliges. I am the administrator so why can it say something like that?

The virtualBox file I downloaded is VirtualBox-3.1.8-61349-Linux_x86.run. What must I type in the terminal using the sudo command to install it. The file is located on my desktop. Will this help if I use the sudo command?

Thanks again

:p

---

### Post by Zzl1xndd on 2011-01-05
Hi Jasper is there a reason you are attempt to install this this way? 

The Methods provided by both Spyderkid and myself are much easier and straight forward.

---

### Post by Japster on 2011-01-05
Thanks for your help

The thing is that I have already downloaded the files. My modem does not have drivers for Linux so I therfore downloaded the Linux files from my Windows. Then I just copied it into my linux.

What I can't understand is why the files can't install if I just double click it like I would in Windows. It is the setup files so I can't understand what is meant with having to be in the root to install the NVidea driver or that I must be the administrator to install the VirtualBox.

Here is the files I downloaded : VirtualBox-3.1.8-61349-Linux_x86.run and NVIDIA-Linux-x86-71.86.14-pkg1.run, can you please tell me, is this how linux setup files look? I'm use to windows setup files so this .run extension is new to me.

Thanks you for your time and patience

:p

---

### Post by Zzl1xndd on 2011-01-05
No problem Jasper .runs are kind of a Generic installer for use with All Linux Distros. 

This Link Should help you with Installing them.

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

For the items that need root open the Terminal (Application > Accessories > terminal) Type in Sudo add a space and then you can drag the file to the terminal (this should fill out the rest of the path, You might need to hit back space once as sometimes this adds an extra space at the end). Then hit enter, it should prompt you for your password and provided you with Root access during the install.

---

### Post by Japster on 2011-01-05
Thanks that helped a lot. I've managed to install the VirtualBox. the NVidea Drivers actually starts installing, but then It stops and says I must disconnect or log out of the X server and then install the driver. How do I log out of the X Server. After logging out of this X server do i just use the Terminal with the sudo command to install the driver?

Thanks for the help :p:p:p

---

### Post by Zzl1xndd on 2011-01-05
hit [CTRL][ALT][F2] (at the same time)

Then type ```
sudo service gdm stop
```

From here you will have to navigate to the file using the Terminal and install (use sudo before it to make sure you have Root).

---

### Post by Japster on 2011-01-05
Thanks a lot guys, you have really helped me a lot.

I appreciate the help


):P):P):P):P

---

### Post by Zzl1xndd on 2011-01-05
Glad we could help out, if everything is fixed then you should mark the thread as Solved.

---

