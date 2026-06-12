---
title: "Totally Stuck, Cannot Boot"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by DrGonzoRIP on 2009-11-22
I'm trying a second thread. I've been stuck for a day and a half now. Yesterday I just rebooted randomly only to have the resolution stuck at 800x600 when it should normally be 1920x1200. The display settings maxed out at 800x600. So, in trying to fix the problem, I've made it worse. Now the system cannot boot. I get the flashing:


Ubuntu 9.10 computername-desktop tty1

computername-desktop login:


From there I reboot in recovery mode. I then followed these directions from another thread:

>                                   **Re: Ubuntu will not boot successfully with 2.6.31 kernel, nor with 2.6.28 kernel**             
                                                                Similar update experience: got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register. tty2 - 6 had the same flashing. tty7 was blank. With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system. Yeah! Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :smile:

5.  ftp[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17. Follow instructions in nVidia installation. Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.Unfortunately the installation failed. I also noticed that now my xorg.conf is now blank. 

Please, please help.

---

### Post by danill2008 on 2009-11-22
I had the same problem, but luckily I had a backup of xorg.conf. The only way (and the easiest) I can think of is to reinstall Ubuntu. Unless you have a backup of xorg.conf somewhere...

---

### Post by DrGonzoRIP on 2009-11-22
> **danill2008 said:**
> I had the same problem, but luckily I had a backup of xorg.conf. The only way (and the easiest) I can think of is to reinstall Ubuntu. Unless you have a backup of xorg.conf somewhere...

I don't have a backup of it. Is there a way to download/install just that?

---

### Post by DrGonzoRIP on 2009-11-22
I guess I'm going to reinstall Ubuntu. Does this mean I will lose my data?

---

### Post by danill2008 on 2009-11-22
What graphics card do u have? Also...I don't think you can download xorg.conf, but you can try mine:

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    1280 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Hope this helps! Otherwise you must do a fresh install;)

---

### Post by danill2008 on 2009-11-22
> **DrGonzoRIP said:**
> I guess I'm going to reinstall Ubuntu. Does this mean I will lose my data?

Not necessarily...You can use the Ubuntu LiveCD and mount your drive with Ubuntu on it. This way you can backup your files under /home or any other location;)

---

### Post by DrGonzoRIP on 2009-11-22
> **danill2008 said:**
> What graphics card do u have? Also...I don't think you can download xorg.conf, but you can try mine:

```

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    1280 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```Hope this helps! Otherwise you must do a fresh install;)

My graphics card is built into my motherboard. It a ASUS [P5E-VM HDMI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237"). It's onboard video chipset is Intel GMA X3500.

---

### Post by DrGonzoRIP on 2009-11-22
> **danill2008 said:**
> Not necessarily...You can use the Ubuntu LiveCD and mount your drive with Ubuntu on it. This way you can backup your files under /home or any other location;)

Is an Ubuntu LiveCD any different from downloading Ubuntu 9.10 and burning it to a CD?

---

### Post by danill2008 on 2009-11-22
> **DrGonzoRIP said:**
> Is an Ubuntu LiveCD any different from downloading Ubuntu 9.10 and burning it to a CD?

That is a Live CD. When you bootup with Ubuntu CD, you will be displayed with "Try Ubuntu without any change to your computer" and "Install Ubuntu". Select the first one. Then you will boot into a live environment. Here you can mount your drive with Ubuntu on it and backup your files:)

---

### Post by DrGonzoRIP on 2009-11-22
> **danill2008 said:**
> That is a Live CD. When you bootup with Ubuntu Cd, you will be displayed with "Try Ubuntu without any change to your computer" and "Install Ubuntu". Select the first one. Then you will boot into a live enviroment. Here you can mount your drive with Ubuntu on it and backup your files:)


That's great, thanks, I'll give it a shot. Still waiting on the download to complete.

---

### Post by DrGonzoRIP on 2009-11-22
Would you mind giving instructions on how to mount the drive? With the way it's been going, I'm sure I will run into complications.

---

### Post by danill2008 on 2009-11-22
Ok no problem...You go'to Places > Computer and double-click on your Ubuntu drive (it should be the one which displays your total HD space and then your Ubuntu volume size e.g "160GB Hard Disk: 84 GB Filesystem". Yours may differ...It may ask for a password, then after that, it's mounted and you can begin backuping your files

---

### Post by DrGonzoRIP on 2009-11-22
> **danill2008 said:**
> Ok no problem...You go'to Places > Computer and double-click on your Ubuntu drive (it should be the one which displays your total HD space and then your Ubuntu volume size e.g "160GB Hard Disk: 84 GB Filesystem". Yours may differ...It may ask for a password, then after that, it's mounted and you can begin backuping your files

Sounds easy enough. Thanks for all your help. It's been a rough couple of days.

---

### Post by danill2008 on 2009-11-22
> **DrGonzoRIP said:**
> Sounds easy enough. Thanks for all your help. It's been a rough couple of days.

It's a pleasure:) After this you can reinstall Ubuntu. I will keep checking this thread, incase you need any help;) Also if this works, mark the thread as solved. It can be found under "Thread Tools".  Good Luck!

---

### Post by DrGonzoRIP on 2009-11-22
The backup process is going well. Hopefully the reinstall does the same.

---

### Post by sandyd on 2009-11-22
> **DrGonzoRIP said:**
> The backup process is going well. Hopefully the reinstall does the same.
why dont you just run
```

sudo cp xorg.conf.original-0 xorg.conf
sudo cp xorg.conf.original xorg.conf

```
that will rest your xorg.conf.

---

### Post by DrGonzoRIP on 2009-11-22
> **carlee said:**
> why dont you just run
```

sudo cp xorg.conf.original-0 xorg.conf
sudo cp xorg.conf.original xorg.conf

```that will rest your xorg.conf.

Too late. I already reinstalled unbuntu, but my resolution is still maxed out at 800x600.

---

### Post by DrGonzoRIP on 2009-11-22
Hey we go again. I got the blinking login again. Hopefully I won't have to reinstall Ubuntu again.

---

### Post by DrGonzoRIP on 2009-11-22
Just reinstalled Ubuntu for the second time today. This is turning into a nightmare. I have tried so many things with no luck. I'm still stuck with 800x600.

---

### Post by DrGonzoRIP on 2009-11-23
Moving to plan b...c... whatever. I'm installing 8.10 instead. At least I knew that worked. Then I'll do the upgrade within the Updater. Also, I'll make sure to backup the xorg.conf. Crossing my fingers.

---

### Post by DrGonzoRIP on 2009-11-23
So I just got done installing 8.10. Now I've gotten the resolution as high as 1360 x 768. Getting closer. What I can't get my head around is how did it work at 1920 x 1200 for so long without any issues. I've reinstalled the OS three times now.

---

### Post by danill2008 on 2009-11-23
> **carlee said:**
> why dont you just run
```

sudo cp xorg.conf.original-0 xorg.conf
sudo cp xorg.conf.original xorg.conf

```that will rest your xorg.conf.

What does this command exactly do? I tried running it, but it says :
```
cp: cannot stat `xorg.conf.original-0': No such file or directory
cp: cannot stat `xorg.conf.original': No such file or directory

```

---

### Post by danill2008 on 2009-11-23
I quickly did a search on your graphics card, [Here]("http://ubuntuforums.org/showthread.php?t=1017077") seems to be something you can try

---

### Post by theozzlives on 2009-11-23
You can boot without changes, hit alt+F2, and type
```
gksu nautilus
```
then copy the live CD's xorg.conf to your X11 folder.

---

### Post by 5mattyb5 on 2009-11-23
Have you tried booting to recovery mode and selecting xfix has worked for me in the past.

---

### Post by DrGonzoRIP on 2009-11-23
> **danill2008 said:**
> What does this command exactly do? I tried running it, but it says :
```
cp: cannot stat `xorg.conf.original-0': No such file or directory
cp: cannot stat `xorg.conf.original': No such file or directory

```

I get the same results with this.

---

### Post by DrGonzoRIP on 2009-11-23
I got it to work briefly on a session by session basis. I followed these instructions:

```
ahmed@ahmed-desktop:~$ cvt 1920 1200 60
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
ahmed@ahmed-desktop:~$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
ahmed@ahmed-desktop:~$ xrandr --addmode VGA "1920x1200_60.00"
ahmed@ahmed-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1920 x 1200
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1920x1200_60.00   59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
ahmed@ahmed-desktop:~$ 



```Now how do I make this permanent?

---

### Post by DrGonzoRIP on 2009-11-23
Any thoughts on adding something to the GDM startup script to get this done?

---

### Post by Sealbhach on 2009-11-23
> **DrGonzoRIP said:**
> Any thoughts on adding something to the GDM startup script to get this done?

Have you tried adding this mode to your xorg.conf?

To edit your xorg.conf do

```
gksudo gedit /etc/X11/xorg.conf

```Then add the option to your xorg.conf. You should add these bits here in red, but of course changing the information to what you have got from xrandr. Ignore all the other stuff in this example xorg.conf, it may not be suitable for you. Just add your new lines in the right section and subsection.


```
Section "Monitor"
        Identifier "HP L1510"
        Option "DPMS"
       [COLOR=Red] Modeline "1024x768" 65.00 1024 1068 1204 1344 768 771 777 806 -hsync -vsync[/COLOR]
EndSection


 Section "Screen"
        Identifier "Default Screen"
        Device "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor "HP L1510"       
        DefaultDepth 24
        SubSection "Display"   
         [COLOR=Red]  Modes "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]
        EndSubSection
EndSection 

 
```

---

### Post by DrGonzoRIP on 2009-11-24
> **Sealbhach said:**
> Have you tried adding this mode to your xorg.conf?

To edit your xorg.conf do

```
gksudo gedit /etc/X11/xorg.conf

```Then add the option to your xorg.conf. You should add these bits here in red, but of course changing the information to what you have got from xrandr. Ignore all the other stuff in this example xorg.conf, it may not be suitable for you. Just add your new lines in the right section and subsection.


```
Section "Monitor"
        Identifier "HP L1510"
        Option "DPMS"
       [COLOR=Red] Modeline "1024x768" 65.00 1024 1068 1204 1344 768 771 777 806 -hsync -vsync[/COLOR]
EndSection


 Section "Screen"
        Identifier "Default Screen"
        Device "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor "HP L1510"       
        DefaultDepth 24
        SubSection "Display"   
         [COLOR=Red]  Modes "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]
        EndSubSection
EndSection 

 
```

Thanks that worked! I also upgraded back to 9.10 w/o any issues yet.

---

### Post by ublintu on 2009-11-24
Can someone check this please: [http://ubuntuforums.org/showthread.php?t=1315876&page=3&highlight=tty1](http://ubuntuforums.org/showthread.php?t=1315876&page=3&highlight=tty1)

---

