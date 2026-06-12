---
title: "Help with nvidia video card setup"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by StonedRaider on 2010-04-27
I have a nvidia 256mb geforce 8400M GS video card. I have recently decided to start changing to ubuntu permanently from windows vista. When I try to launch call of duty world at war through wine it come up with the following
[IMG]http://file050a.bebo.com/10/original/2010/04/28/02/6379298933a12464506977o.jpg

Samilar errors happen with other games as well. Was wondering if anyone could help with this problem? Have already done a google search and gave it my best shot. I am currently using juanty, ubuntu 9.04.
[IMG]file:///home/tobin/Desktop/Screenshot.png[/IMG][IMG]file:///home/tobin/Desktop/Screenshot.png

---

### Post by Revolutionary101 on 2010-04-27
1. Did you install the graphics driver for the graphics card?

2. COD World at War may not work in Wine. Wine will not run every single game that works on Windows. It may run some games like World of Warcraft but not all games. I personally haven't tried COD World at War on Ubuntu but I hope you can get it working.

---

### Post by StonedRaider on 2010-04-27
Not to sure on where to download the driver? Tried downloading it form nvidia, but had absolutely no idea what to open the file with?

---

### Post by v1ad on 2010-04-27
try enabling proprietary drivers in System > Administration > Hardware Drivers.

---

### Post by limey_rick on 2010-04-27
If you go to NVIDIA, you can download the driver from here: 

[http://www.nvidia.com/object/linux_display_ia32_195.36.15.html](http://www.nvidia.com/object/linux_display_ia32_195.36.15.html)

For 64bit, here: [http://www.nvidia.com/object/linux_display_amd64_195.36.15.html](http://www.nvidia.com/object/linux_display_amd64_195.36.15.html)

I don't know how old your graphics card is, but if its not legacy (very old), then these are the drivers you'll likely need. 

The file is a UNIX shell script, so when you've downloaded it, you'll want to open a terminal and then cd to the directory where it was saved then type 

> sudo sh NVIDIA-Linux-x86-195.36.15-pkg1.run

and then follow the prompts. This may or may not get you very far, but it will get you started. If may need other packages to compile but I think if memory serves me well, it will tell you. If not post what you get.

---

### Post by StonedRaider on 2010-04-28
I enabled the driver through system>administrator>Hardware Drivers. Tried to launch COD but it failed, I don't think wine will run it. I tried it on GTA and it worked. Graphics were going pretty badly, it was slow and glitchy. So I gave downloading the graphics from nvidia a try and it keeps saying that i have an X server enabled and i that I need to exit it.

---

### Post by 3rdalbum on 2010-04-28
WaW doesn't work on Wine.

---

### Post by StonedRaider on 2010-04-28
I know, but GTA isn't running well at all. Very slow and glitchy?

---

