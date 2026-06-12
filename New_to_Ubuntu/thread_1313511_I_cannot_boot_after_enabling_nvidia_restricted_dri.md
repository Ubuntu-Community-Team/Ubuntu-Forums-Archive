---
title: "I cannot boot after enabling nvidia restricted driver in karmic"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by steven_liauw on 2009-11-03
Hi,

I'm quite new to linux and ubuntu, although I am proficient with Windows. I've switched to Ubuntu for my home compter about 3 months now. Along with everybody else, I downloaded the 9.10 version, and installed it new on my computer.

My computer is has an ECS P4M800 motherboard, and Nvidia GeForce 5500 256 MB AGP graphic cards, 1 GB of memory, Pentium Dual Core processor.

Everything was fine at the installation. No problem downloading, and installing the softwares I wanted. However, when I wanted a little animation for my desktop, it prompted me to enable the nvidia restricted driver, which I did. I then had to reboot.

Then, I cannot get into ubuntu anymore. The screen will show the white circle, and then the screen will take me to a text login, but the whole screen will be flashing on and off. First it asks for the login username. It's very hard to type, because the screen is flashing all the time. After much difficulty I can type my username, but after that it asks for the password, and it is just impossible to enter the password, because the letters do not show as you type it.

Well, at first I figured that somehow the driver was not installed correctly. So, at GRUB, I chose to enter "recovery mode" and then from somewhere in the internet I tried this line:
sudo apt-get install nvidia-185-kernel-source

It was just a wild try. I don't relish working with command lines, but if I have to, then I'll do it.

It then downloaded and installed...but it worse now. It won't take me to the text login anymore, and I can't even get into GRUB.

My question: is the nvidia restricted driver incompatible with 9.10?
Did I do something wrong?
Is there anything I can do now to undo / uninstall the driver?
I figure that the easiest way to do it would be to reinstall. But besides taking time, I want to learn more about ubuntu, where I went wrong, etc.

Thanks for any input. (Sorry if this issue is already posted somewhere).

---

### Post by overdrank on 2009-11-03
Moved to Absolute Beginner Talk

---

### Post by hansdown on 2009-11-03
Hi steven_liauw.

If you can get to the desktop, click system> administration> hardware drivers.

It should scan for the driver your system needs.

Maybe run update manager first if you can.

---

### Post by steven_liauw on 2009-11-03
Thanks for the quick reply,

I cannot get into the desktop. That's the problem.

---

### Post by hansdown on 2009-11-04
Sorry about that.

Can you boot the live CD, and choose safe graphics?

I'm using the 173 driver right now, which is the one that was offered to me from the hardware drivers option.

---

### Post by steven_liauw on 2009-11-04
I can boot the live cd just fine.

The original install was also ok. It was only after enabling the nvidia restricted drivers (I'm not sure which version, but I think it's 17x..) that I cannot enter X anymore. All I got was the flashing text-based login with black background.

---

### Post by perw on 2009-11-04
Hi

I had the same set of problems after upgrading from 9.04. After upgrade and first boot I got a couple of text lines ending with a standard text based login prompt. The lines were flickering and it was almost impossible to enter my userid, the system seemed to be occupied with something else. 

I ended up downloading the latest Linux driver (190.42) from Nvidia.com down to a USB-stick, then booting in recovery mode from the Ubuntu alternate CD and installing the Nvidia driver from the stick (it's just a shell-script that does the necessary install and kernel linking). 

There is a potential problem that the Nvidia sw doesn't show up as installed when checking in Synaptic or in the Hardware Drivers but at least it works and so does Compiz. 

My laptop is a Fujitsu-Siemens Lifebook E8420 which contains a Nvidia GeForce 9300M GS card/chip.

IMHO the 9.10 distribution should have been tested more thoroughly before being released

---

### Post by hansdown on 2009-11-04
perw's sounds good.

---

### Post by mkisow on 2009-11-12
Were you able to fix this?  If so was it an xorg.conf issue, if it was can you please post your xorg.conf?

---

### Post by tbob18 on 2009-11-13
I have the same problem, I also tried the new 190.42 as well and it did the same thing my specs are as follows:

Sony VGN-Z610YB
GPU's are: 9300M GS + Intel 4500MHD

It would be nice if I could get this working..

---

### Post by mkisow on 2009-11-13
Now, I have read other threads where it works fine in the 2.6.28 kernel however I have come over from debian "Lenny" I know their repo's but not Ubuntu's how can I grab the 2.6.28 kernel without moving forward with reinstalling with 9.4?

This is evidently an issue w/ the 2.6.31 kernel.

---

