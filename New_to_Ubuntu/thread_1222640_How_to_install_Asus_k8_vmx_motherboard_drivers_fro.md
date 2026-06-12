---
title: "How to install Asus k8 vmx motherboard drivers from CD in Ubuntu 9.04"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Prabhs on 2009-07-25
Hi guys ,

I am Prabhdeep Singh from India, An absolute beginner in Linux, just migrated from Windows XP and installed Ubuntu 9.04 few days ago . The problem I am facing is that I don't know how to install applications, or other downloaded softwares with tarballs tar.gz and tar.bz2 In Linux.

I wanna install my mother board drivers but dont have any idea how to start.The hardware I,ve got is AMD 3000+ processor , Asus K8V-MX MotherBoard.
I am providing the details of the drivers 


DISPLAY DRIVERS  contains

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044

1.
Drivers/Display---- containsfolders-
                                        red hat 9-
                                                       k8m800xf0044--(It contains the files)
                                                                  RedHat/9.0/k8/0libddmpeg.so
                                                                  RedHat/9.0/k8/via.o   
                                                                  RedHat/9.0/k8/via_drv.o     
                                                                  RedHat/9.0/k8/via_v4l_drv.o   
                                                                  RedHat/9.0/k8/videodev.o

2.

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044/Utility
                                                             gtkthemes 
                                                             lib
                                                             s3utility
                                                             pixmaps
                                                             utility_install
                                                             utility_uninstall

3.

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044/AppNotes.txt 

4.

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044/Installation.txt

5.

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044/vinstall

6.

/media/cdrom0/Drivers/Display/Linux/RedHat9/k8m800xf0044/K8MXF40044/vuninstall



AUDIO DRIVERS  contains

/media/cdrom0/Drivers/Audio/linux

1.
/media/cdrom0/Drivers/Audio/linux/alsa-driver-1.0.9b.tar.bz2

2.
/media/cdrom0/Drivers/Audio/linux/alsa-lib-1.0.9.tar.bz2

3.
/media/cdrom0/Drivers/Audio/linux/alsa-utils-1.0.9a.tar.bz2


FAST RHINE ETHERNET DRIVERS  contains
/media/cdrom0/Drivers/LAN/LINUX

1.
/media/cdrom0/Drivers/LAN/LINUX/linux.txt

2.
/media/cdrom0/Drivers/LAN/LINUX/rhinefet.tgz



Apart from these files i 've also downloaded Firefox 3.5.1 and eclipse-jee-galileo-linux-gtk.tar.gz and other java softwares.

Please guide me to install them . I am not good at using terminal/cmd.:(

Thanks


Prabhdeep Singh

---

### Post by yeats on 2009-07-25
> Hi guys ,

I am Prabhdeep Singh from India, An absolute beginner in Linux, just migrated from Windows XP and installed Ubuntu 9.04 few days ago . The problem I am facing is that I don't know how to install applications, or other downloaded softwares with tarballs tar.gz and tar.bz2 In Linux.

I wanna install my mother board drivers but dont have any idea how to start.The hardware I,ve got is AMD 3000+ processor , Asus K8V-MX MotherBoard.
I am providing the details of the drivers

Hi Prabhdeep,

Sounds like you have some research to do.  I would assume that most of what you're trying to install here is already included.  Is something not working?

The main method for installing software in Ubuntu is the Synaptic Package Manager (from the top menu bar: System -> Administration -> Synaptic Package Manager).  From there you can search for software packages and install them as you see fit.  There's no need for going to the internet and finding tar.gz packages to manually install.

Check out the Sticky links in the Absolute Beginner forum.  You will greatly benefit from reading these resources before continuing.

Good luck!

---

### Post by 3rdalbum on 2009-07-25
Usually, your motherboard's drivers are included in the kernel. If you have sound and your Ethernet port works, then you have no need for the contents of your "driver install" disc.

Same with your video driver. If you get a good image on the screen, then your video driver is installed.

I recommend installing software from Synaptic Package Manager or Add/Remove Applications, rather than downloading software from the Internet. If you must do it, then follow the instructions given with the program because not all programs are installed or compiled in the same way.

---

### Post by Prabhs on 2009-07-27
> **chrissharp123 said:**
> Hi Prabhdeep,

Sounds like you have some research to do.  I would assume that most of what you're trying to install here is already included.  Is something not working?

The main method for installing software in Ubuntu is the Synaptic Package Manager (from the top menu bar: System -> Administration -> Synaptic Package Manager).  From there you can search for software packages and install them as you see fit.  There's no need for going to the internet and finding tar.gz packages to manually install.

Check out the Sticky links in the Absolute Beginner forum.  You will greatly benefit from reading these resources before continuing.

Good luck!


I have come to know that i ve got openchrome drivers installed along with ubuntu but still i am feeling uneasy with it so I would like to install the unichrome drivers that comes along with my mother board cd .kindly help me out in installing them directly from cd itself .i want to know what commands to use from terminal to access the files in it .I 've already mentioned the details along with the path .

Thanks...

---

### Post by Prabhs on 2009-07-27
> **3rdalbum said:**
> Usually, your motherboard's drivers are included in the kernel. If you have sound and your Ethernet port works, then you have no need for the contents of your "driver install" disc.

Same with your video driver. If you get a good image on the screen, then your video driver is installed.

I recommend installing software from Synaptic Package Manager or Add/Remove Applications, rather than downloading software from the Internet. If you must do it, then follow the instructions given with the program because not all programs are installed or compiled in the same way.

Thanks for replying buddy.......:P

Actually audio driver works perfectly but I still think that there is some problem with the video drivers It gives me exactly same feeling like the one having video drivers not installed in windows and these drivers are the VIA/S3G unichrome meant for  K8M800 chipset  which has the files like vinstall (already mentioned with the path ). Kindly tell me the commands to install it in an easy way . As I am very much impressed with Ubuntu So i would like it to be installed on various machines in some institutions so I would like to know  a general way so that I can use that method on any machine where possibility of computers to be  Online   is difficult. If you want I can give you the instruction file that came with it on topic for Installation but i am sorry to say that I couldn't understand that .

Thanks and waiting for a quick reply....

---

### Post by bailbath on 2009-07-27
Via chrome can be a pain but it is possible. Linux is a moving target so those drivers on the cd maybe outdated or improved so I would do some google research or there maybe somebody here with a solution. I did have a laptop with the same chipset and I was successful in installing a driver but not from a cd from the internet i just can't remember what I did I will hve a look round the net and get back if I remember how I did it!

---

### Post by bailbath on 2009-07-27
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

[http://www.hombrepac.com.ar/software-libre/howto-via-chrome9-igp-on-ubuntu-linux/](http://www.hombrepac.com.ar/software-libre/howto-via-chrome9-igp-on-ubuntu-linux/)

Couple of links for you.



Remember that this is not a very powerful chipset but you can get some success with it. If you can afford it why not get a video card for your pc do some research and find the card that works well with ubuntu and is good for yourself.
As for your other questions there are better ways to install what you want and again I would use some of the sticky's above as a guide. Have fun.

---

