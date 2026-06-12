---
title: "Input not support"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by telovin on 2009-11-16
Hi I am new to ubuntu and recently installed 9.10 version. After installation when booting up, gets an error input not support. It just sits there forever. I am using NEC LCD170wv
After booting up i am unable to see  the screen.All i see is coloured grids and a box saying input not support. Please help

---

### Post by ukripper on 2009-11-16
> **telovin said:**
> Hi I am new to ubuntu and recently installed 9.10 version. After installation when booting up, gets an error input not support. It just sits there forever. I am using NEC LCD170wv
After booting up i am unable to see  the screen.All i see is coloured grids and a box saying input not support. Please help

Can you boot into 9.10 live cd ok?

---

### Post by telovin on 2009-11-17
i did not boot from live cd, i installed ubuntu-9.10-desktop-i386.iso and had the option of choosing win xp or ubuntu, chose ubuntu saw ubuntu logo and then it shows color grids and the message comes"input not supported" it wont evn say supported it says input not support. After choosing ubuntu i went to normal mode safe graphic mode n in everything i am getting the same error. I went to the command line but dont know what command to put in. I read some posts saying to put the sudo command but i cant see the desktop so sont know how to reach the terminal.
 
the details of videocard are:
 
NVIDIA System Information report created on: 11/17/2009 15:22:23
System name: VINU
[Display]
Processor:  AMD Sempron(tm) Processor LE-1250 (2200 MHz)
Operating System: Microsoft Windows XP, 32-bit (Service Pack 3)
DirectX version: 9.0c
GPU processor:  GeForce 7025 / nForce 630a
Driver version:  190.38
Core clock:  425 MHz 
Memory clock:  100 MHz (200 MHz data rate) 
Memory interface: 32-bit 
Memory:   512 MB
Video BIOS version: 5.67.32.25.00
IRQ:   22
Bus:   FPCI
[Components]
nvCplUIR.dll  1.5.2400.10  NVIDIA Control Panel
nvCpl.cpl  2.7.130.16  NVIDIA Control Panel Applet
nvExpBar.dll  1.5.2400.10  NVIDIA Control Panel
nvCplUI.exe  2.7.130.16  NVIDIA Control Panel
nvWSSR.dll  6.14.11.7516  NVIDIA Workstation Server
nvWSS.dll  6.14.11.9038  NVIDIA Workstation Server
nvViTvSR.dll  6.14.11.7516  NVIDIA Video and TV Server
nvViTvS.dll  6.14.11.9038  NVIDIA Video and TV Server
nvMoblSR.dll  6.14.11.7516  NVIDIA Mobile Server
nvMoblS.dll  6.14.11.9038  NVIDIA Mobile Server
nvDispSR.dll  6.14.11.7516  NVIDIA Display Server
NVMCTRAY.DLL  6.14.11.9038  NVIDIA Media Center Library
NVOGLNT.DLL  6.14.11.9038  NVIDIA Compatible OpenGL ICD
nvDispS.dll  6.14.11.9038  NVIDIA Display Server
NVCPL.DLL  6.14.11.9038  NVIDIA Compatible Windows 2000 Display driver, Version 190.38 
NV4_MINI.SYS  6.14.11.9038  NVIDIA Compatible Windows 2000 Miniport Driver, Version 190.38 
NV4_DISP.DLL  6.14.11.9038  NVIDIA Compatible Windows 2000 Display driver, Version 190.38 
NVCUDA.DLL  6.14.11.9038  NVIDIA CUDA 2.3 driver
nvGameSR.dll  6.14.11.7516  NVIDIA 3D Settings Server
nvGameS.dll  6.14.11.9038  NVIDIA 3D Settings Server

---

### Post by ukripper on 2009-11-17
can you boot into ubuntu live cd and tell me if the same error comes up? I think problem could be related to you monitor's refresh rate. Can you boot in live cd and we go from there.

---

### Post by telovin on 2009-11-17
ok will do that.

---

### Post by telovin on 2009-11-17
I tried to boot from live cd. I tried all the options like try ubuntu without anychanges to your computer, install ubuntu,check disk for defects,test memmory and boot from first harddisk.. but I am getting the error input not support. Checked disk for defects, dint find any, memmory test dint show any errors. when tried live option as well as the install option, getting the same colored grids and input not support.

---

### Post by telovin on 2009-11-18
Today am able to boot up from live cd by typing usplash instead of splash or by unchecking noacpi. But I have to do each time I boot the live cd and it wants me to install nvidia drivers i do it and again next time when i restart, it doesnt recognise the nvidia isntalled.

---

### Post by ukripper on 2009-11-18
> **telovin said:**
> Today am able to boot up from live cd by typing usplash instead of splash or by unchecking noacpi. But I have to do each time I boot the live cd and it wants me to install nvidia drivers i do it and again next time when i restart, it doesnt recognise the nvidia isntalled.

Yes live cd changes are not persistent changes. live cd is only to test if things are working at that instance. So that means changes you made with live cd should now be applied to your current ubuntu installation.

Now boot into your normal ubuntu installtion and apply sam echanges you applied during live cd.

---

### Post by telovin on 2009-11-19
it is not working with ubuntu installed version....... when i do usplash or add vga=791(both in safegraphic mode) or inacpi worarounds if i add acpi=on, still it wont work. From live cd i was able to boot only from safe graphic mode provided i make these changes each time i login..

---

### Post by ukripper on 2009-11-19
See this thread here -  [http://ubuntuforums.org/showthread.php?t=1329428](http://ubuntuforums.org/showthread.php?t=1329428)

Follow my posts #7 and #9

---

### Post by telovin on 2009-11-20
Hello ukripper,
I triedcvt1600120060 after booting in to livecd, I got
ubuntu@ubuntu:~$ cvt 1600 1200 60
# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync


and when i type sudo nano /etc/X11/xorg.conf, Iget this screen.


ection "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Horisync        49.0-74.0
        VertRefresh     60.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

I configured, saved and did exit, but after rebooting, its the same.Once i came back and checked in the live cd terminal, it was like before as if it was not configuered .I did it 2-3 times but still the same. also one of my hard drives is free, if this is not working, could you guide me as to how to do the partition and reinstall instead of wubi?

---

### Post by ukripper on 2009-11-20
> **telovin said:**
> it is not working with ubuntu installed version....... when i do usplash or add vga=791(both in safegraphic mode) or inacpi worarounds if i add acpi=on, still it wont work. From live cd i was able to boot only from safe graphic mode provided i make these changes each time i login..

ok there are two different issues that means one is you can't boot at all and another one is input not supported?

Are you getting any error messages when you boot? what happens when you reach at login screen do you get that message "input not suppoted" even before that. does is it give you black screen prompting for your username?

---

### Post by telovin on 2009-11-20
when i put in the live cd i am able to see all the following options:
try ubuntu without anychange to your computer
install ubuntu
checkdisk for defects
test memmory
boot from 1st harddisk

If I choose try ubuntu withou tany chnage then i get input not support. 
Before choosing that option, i go to f4, choose safe graphic mode and then f6 and then press enter at the option acpi=off(if i press enter at that option, a cross mark is added to that) and then come back to try ubuntu without any change, it loads..whenever it loads, asks me to install NVIDIA 173 or 185. I have NVDIA 191 on my PC.

If i try booting ubuntu (wubi) from hard disk(in all modes) i get input not support. I see the ubuntu logo which sits there for sometime and then the error message input not support with coloured grids come up. It wont ask me for my user name and password. I tried editing the command lines of hard disk ubuntu on safe mode (like splash,usplash,vga=791) but no luck.

---

### Post by ukripper on 2009-11-20
> **telovin said:**
> 

If i try booting ubuntu(wubi) from harddisk(in all modes) i get input not support. I tried editting the command lines of harddisk ubuntu on safemode (like splash,usplash,vga=791) but no luck.

ok when you boot from hardisk, do you get input not supported at very beginning which is after grub screen or it does take you to somewhere?

---

### Post by telovin on 2009-11-20
when i boot from hardisk and click on ubuntu, i get to choose from different installation press esc. So i press esc and choose normal mode(it doesnot make a differnce if i do it or dont do it) and then i get a black screen with many scripts running and at the end i get setting up key maps etc... n then the screen with coloured grids and input not support error comes up.

---

### Post by ukripper on 2009-11-20
> **telovin said:**
> when i boot from hardisk and click on ubuntu, i get to choose from different installation press esc. So i press esc and choose normal mode(it doesnot make a differnce if i do it or dont do it) and then i get a black screen with many scripts running and at the end i get setting up key maps etc... n then the screen with coloured grids and input not support error comes up.

ok when it gets there:
Can you press CTRL + ALT +F1 and put your username and password and type below command and post output here:
```
xrandr
```

---

### Post by telovin on 2009-11-20
I am unable to load my win xp or ubuntu, onlyway i can see my desktop is loading through this livecd. I can see all my data in my harddrives once ubuntu loads.(unfortunately, i didnt take a back up of my data)

I tried ur xrandr while booting live cd .First did ctrl+alt+f1 but didnt ask for username and password. I typed xrandr and nothing happend.

Could you please help me in installing ubuntu to one of my free hradrives? if i format all i migfht loose my data. I have all my notes on my documents and my exams are in dec..

I tried installling ubuntu to one of my free harddrive now but gets a message saying no rootfile system selected..(may be this step messed up my windows boot as well). Anyway i can install to that drive so that I can save my data?

---

### Post by telovin on 2009-11-20
I manged to get past that no root file system selected and installing ubuntu on my free harddrive.. hope i can boot up successfully..

---

### Post by telovin on 2009-11-20
Hi ukripper,
I was able to install ubuntu onto my freehardrive successfully and guess what I am able to boot up to windows xp as well and all my data is still there. I partitioned only one of  my free drive.. Now no error messages, grub manager loads ubuntu 9.10 smoothly and I am writing this message from installed ubuntu.. :) I am EXCITED! Thanks a lot for all ur help!:D

---

### Post by ukripper on 2009-11-23
> **telovin said:**
> Hi ukripper,
I was able to install ubuntu onto my freehardrive successfully and guess what I am able to boot up to windows xp as well and all my data is still there. I partitioned only one of  my free drive.. Now no error messages, grub manager loads ubuntu 9.10 smoothly and I am writing this message from installed ubuntu.. :) I am EXCITED! Thanks a lot for all ur help!:D

Nice one. i am glad it worked out for you.

---

