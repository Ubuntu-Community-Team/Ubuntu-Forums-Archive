---
title: "Ubuntu Wont LOAD"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by conrad77 on 2009-11-29
I am very new to this whole Linux thing and want to start getting more into it. To start off I loaded ubuntu in a virtual PC on my W7 laptop, and it worked fine. For fun I found an old computer at my parents house and thought it would be fun to install ubuntu on that, but it has been a major headache. 

I have successfully burned the ISO image and have set the old desktop to boot off of that. From there I hit install ubuntu, the computer thinks for a little bit then the screen just goes black, but the computer is still on and thinking. I thought there might be a problem with the monitor since it was an old one, so I connected it to my flat panel tv and the same problem happened. I then thought there might be a problem with my graphics card, so i installed an old ATI graphics card, and the same thing happend. The computer is an old IBM NetVista desktop, I fear the problem is a lot more technical than I expected and was wondering if anyone has any advice on what to do.

thanks.

---

### Post by halitech on 2009-11-29
How much ram does the old IBM have? Also, if you are trying 9.10, you will probably have better luck using whatever the onboard video is then an old ati card.

---

### Post by Merk42 on 2009-11-29
Do you know the processor speed, hard drive space and ram of the computer you're trying to install on?

[The recommended requirements are:](https://help.ubuntu.com/community/Installation/SystemRequirements)[list]
[*]700 MHz x86 processor
[*]384 MB of system memory (RAM)
[*]8 GB of disk space
[*]Graphics card capable of 1024x768 resolution [/list]

---

### Post by conrad77 on 2009-11-29
okay the system has a Pentium III processor at 933/133 MHz
384 MB of system memory
IDE HD with 20 GB free
and the ATI MACH64 graphics card

---

### Post by halitech on 2009-11-29
will a 1 or 2 meg video card even do 1024x768 resolution?

the Mach64 cards were the bomb when they came out but by todays standard, they are garbage. At most they had 8meg of video memory and only 2d support so even if you can get it running, don't expect miracles out of the video performance.

---

### Post by mlentink on 2009-11-29
> **halitech said:**
>  At most they had 8meg of video memory and only 2d support so even if you can get it running, don't expect miracles out of the video performance.

No, but they ***will*** display a GUI.

I like to make two suggestions.

1. Use the alternate disk to install (non GUI, bit you can install it afterwards). The GUI installer needs 384MiB to install, but that excludes video-memory. 
2. Use a light weight version, like Xubuntu

---

### Post by conrad77 on 2009-11-29
should i consider another graphics card, I just really want to get this running, its going to be used mostly to experiment with linux and possibly set up as a firewall/router for my home network.

thanks all!

---

### Post by halitech on 2009-11-29
> **mlentink said:**
> No, but they ***will*** display a GUI.

I like to make two suggestions.

1. Use the alternate disk to install (non GUI, bit you can install it afterwards). The GUI installer needs 384MiB to install, but that excludes video-memory. 
2. Use a light weight version, like Xubuntu

I agree, gui is possible but but its not going to be a snappy machine running Ubuntu. Xubuntu or doing a minimal install and putting LXDE on might work better.

> **conrad77 said:**
> should i consider another graphics card, I just really want to get this running, its going to be used mostly to experiment with linux and possibly set up as a firewall/router for my home network.

thanks all!

If you have another card (I'm guessing only PCI slots on the motherboard) that fits, might be an idea but depending on what you have for expansion slots will determine what you can do.

---

### Post by conrad77 on 2009-11-29
The motherboard does have 3 PCI slots and one AGP connector. 

Whats the difference between ubuntu and xubuntu? is there a disadvantage of running xubuntu?

---

### Post by halitech on 2009-11-29
If you can find an AGP card then I would use it, an old Nvidia would be ideal if you can find one.

The main difference is the layout and look and the applications that each install by default. Ubuntu will install Open Office but Xubuntu will install AbiWord and Gnumeric. Xubuntu aims to be a lighter based distro for lower end speced machines.

---

