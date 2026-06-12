---
title: "installing GeForce2 MX/MX 400 ubuntu  10.10"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by joham34 on 2010-12-15
Hi everybody 
I have an old pc ( pentium 4 1,5 ghz , 760 mB ram (Rimm) with a GeForce2 MX/MX 400 VGA and a modern Flatron LG monitor . I recently installed ubuntu 10.10 on it and it runs with acceptable speed but the screen resolution is quite low (800x600) . Nouveau driver is installed. I tried to install legacy 96.43.18 driver from both the command line and synaptic but although the procedure is referred as successful , nothing changes (after rebooting) and from the system-administration-additional drivers I get : driver is activated but not currently in use. When I blacklist nouveau I get even lower resolution, I get the nvidia configuration tool where I get the  message 
" You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server ". 
 lspci -v returns that the module used is nvidia (instead of nvidia-96 which is only listed) 
So 1) Would nvidia driver be faster than nouveau? 2) would higher resolution slow down my pc ? and 3) How can I activate it? 
any help would be appreciable, googling the problem didnt help much

---

### Post by lykwydchykyn on 2010-12-15
I have one of those cards to in one of my machines.  For Maverick you actually need the 96.43.19 which nvidia released a few months after Maverick came out (which is why it's not installed by default).

The nvidia driver definitely gives better performance than nouveau.  Download the latest legacy 96.xx driver from nvidia's website and follow their instructions for installation.

---

### Post by joham34 on 2010-12-15
> **lykwydchykyn said:**
> I have one of those cards to in one of my machines.  For Maverick you actually need the 96.43.19 which nvidia released a few months after Maverick came out (which is why it's not installed by default).

The nvidia driver definitely gives better performance than nouveau.  Download the latest legacy 96.xx driver from nvidia's website and follow their instructions for installation.

Thank you , I installed 96.43.19 successfully but the problem now is that I cant get display because the frequency is out of range ( 68.6/85 ) I run fail safe mode and gedit nvidia-xconfig but there is not an option (at least an obvious one ) to adjust monitor frequency . 
Any idea how to do it ?

---

### Post by lykwydchykyn on 2010-12-15
That can happen when the video resolution goes higher than the monitor can handle.  You probably need to generate an /etc/X11/xorg.conf file and hard-code a lower resolution in.  You can also enter correct hsync and vsync ranges in there, it might help.

I don't know how intimidating that sounds to you, but these wiki pages may get you going in the right direction:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

### Post by joham34 on 2010-12-18
> **lykwydchykyn said:**
> I have one of those cards to in one of my machines.  For Maverick you actually need the 96.43.19 which nvidia released a few months after Maverick came out (which is why it's not installed by default).

The nvidia 96.43.19 driver is definitely faster than nouveau.  Download the latest legacy 96.xx driver from nvidia's website and follow their instructions for installation.

Thanks for your guidance . I had to struggle a little bit but finally after some effort and after changing some values in xorg.conf , I managed to get picture and then it was easy to set properly the resolution from nvidia xserver settings tool . 
I also had to deactivate compiz (I dont use it anyway ) and now 10.10 Rocks ! 
Thanks again , I'll makr thread as solved

---

### Post by zeppfrog on 2011-01-04
how about sharing the step by step, I am breathing new life into an old pc myself with the geforce2 mx400

---

### Post by air-t on 2011-01-06
Hi 2 all, this is my first post :)

After looooong time with red eyes i DID IT!!!! 
hope this help you

i have old video card **GeForce 2 MX-400 64Mb** and Ubuntu 10.10

1. download this driver ( [http://www.sendspace.com/file/n79rwg](http://www.sendspace.com/file/n79rwg) ) and put it to your home directory (for example: /home/air-t/nv.run)
2.  i go to ubuntu app center and install Nvidia X.ORG (version 185) driver. 
3. ater install i reboot my computer and ubuntu starts in console mode without graphic and other modes
4. login as root and type (**sudo sh nv.run**) go step by step ... and OMG .. all installed without errors!
5. after install you must reboot and enjoy. All resolutions and OpenGL :) 

Ubuntu ROCK! :guitar:

---

### Post by esrom02 on 2011-07-10
**help me please, I'm having the same problem but the thing is, even at my very first boot, I don't have any display, its just plane white. I can't follow any of the instructions here, can anyone teach me how to use the text mode of ubuntu and guide me how to do the instructions given here by using only terminal?**

---

### Post by opal_shilin on 2011-12-27
> **air-t said:**
> Hi 2 all, this is my first post :)

After looooong time with red eyes i DID IT!!!! 
hope this help you

i have old video card **GeForce 2 MX-400 64Mb** and Ubuntu 10.10

1. download this driver ( [http://www.sendspace.com/file/n79rwg](http://www.sendspace.com/file/n79rwg) ) and put it to your home directory (for example: /home/air-t/nv.run)
2.  i go to ubuntu app center and install Nvidia X.ORG (version 185) driver. 
3. ater install i reboot my computer and ubuntu starts in console mode without graphic and other modes
4. login as root and type (**sudo sh nv.run**) go step by step ... and OMG .. all installed without errors!
5. after install you must reboot and enjoy. All resolutions and OpenGL :) 

Ubuntu ROCK! :guitar:

hi 'air-t', I want to ask whether the way it works for ubuntu 11.10 ?

---

### Post by dapeios on 2012-06-30
i have to ask, does it work on ubuntu 12.04, i have that same problem with the grafics, also the s-video output does not work.

thanks in advance for the help

---

### Post by oldos2er on 2012-06-30
Old thread closed. Please start a new thread for your question.

---

