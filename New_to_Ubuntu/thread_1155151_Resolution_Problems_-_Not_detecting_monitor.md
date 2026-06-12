---
title: "Resolution Problems - Not detecting monitor"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by FroogleDoop on 2009-05-10
Ubuntu is only offering me two different resolutions (800x600 and 640x480), and cannot detect my monitor. I've installed Ubuntu on a number of my laptops, and have never had this particular problem. I've read a lot online which details that I have to go into xorg.conf to edit/fix this issue, but I have little understanding of the command line/Linux in general. A friend of mine simply put this on here for me. Is there any way to fix this? I apologise if this is a very basic question.

---

### Post by SunnyRabbiera on 2009-05-10
Yipes, what version of ubuntu are you running?
Is this a laptop or desktop?
If you are using Ubuntu versions 9.04 and 8.10 then its to be expected, ever since displayconfig-gtk was removed trying to get good resolution has been made harder then it should be.

---

### Post by FroogleDoop on 2009-05-10
The problem is on m desktop. My laptops have never had this problem, even with the newer versions.

I currently have the newest version on my desktop (which is the computer having the problem.)

---

### Post by overdrank on 2009-05-10
> **FroogleDoop said:**
> Ubuntu is only offering me two different resolutions (800x600 and 640x480), and cannot detect my monitor. I've installed Ubuntu on a number of my laptops, and have never had this particular problem. I've read a lot online which details that I have to go into xorg.conf to edit/fix this issue, but I have little understanding of the command line/Linux in general. A friend of mine simply put this on here for me. Is there any way to fix this? I apologise if this is a very basic question.

Hi and welcome, to add to SunnyRabbiera questions there is also booting into recovery mode and using the xfix option.

---

### Post by FroogleDoop on 2009-05-10
What?

---

### Post by overdrank on 2009-05-10
> **FroogleDoop said:**
> What?

Sorry :oops: should have given more details. Recovery mode is usually the second choice from the grub when booting. Once in recovery mode you should be given 4 options of which you can choose xfix. After xfix is complete you should be given the 4 options again where you can boot normally. Hopefully this will correct the graphical issues. 
Also if you can tell us the model of the graphics card this may help. 
Also look under system, administration, hardware drivers to see if any drivers are available

---

### Post by FroogleDoop on 2009-05-10
I honestly know very little about the command line. I only have Linux on my computers because my friends have me do it.

I have an NVIDIA GeForce 9500 GS and a HP 20" Widescreen Flat-Panel TFT-LCD HD Monitor.

There were drivers available under Hardware drivers, but it wouldn't allow me to activate any of them.

---

### Post by overdrank on 2009-05-10
> **FroogleDoop said:**
> I honestly know very little about the command line. I only have Linux on my computers because my friends have me do it.

I have an NVIDIA GeForce 9500 GS and a HP 20" Widescreen Flat-Panel TFT-LCD HD Monitor.

There were drivers available under Hardware drivers, but it wouldn't allow me to activate any of them.

Does it give a error when trying to enable the drivers? And you have Internet connection?

---

### Post by FroogleDoop on 2009-05-10
No, it just kind of stops trying. When I enable the driver, it'll show a dialogue saying "downloading and installing" with a percentage bar below it. Soon after, it disappears, and the percentage never went up fron zero.

---

### Post by overdrank on 2009-05-10
> **FroogleDoop said:**
> No, it just kind of stops trying. When I enable the driver, it'll show a dialogue saying "downloading and installing" with a percentage bar below it. Soon after, it disappears, and the percentage never went up fron zero.

Ok try and update first. System, administration, Update manager and click the check and then apply any updates. Then try to enable the drivers again.

---

### Post by FroogleDoop on 2009-05-10
No upgrades.

---

### Post by FroogleDoop on 2009-05-10
Although there were no upgrades, the fact that I checked convinced the system to let me download the driver, and all is well. Thanks for helping me out :)

---

### Post by overdrank on 2009-05-10
> **FroogleDoop said:**
> Although there were no upgrades, the fact that I checked convinced the system to let me download the driver, and all is well. Thanks for helping me out :)

Great I was running out of ideas without going to command line. :)

---

### Post by FroogleDoop on 2009-05-10
I do know a few commands here and there for the command line, just nothing too extensive. I had arch for a while, and simply couldn't take it.

---

### Post by presence1960 on 2009-05-10
> **FroogleDoop said:**
> I honestly know very little about the command line. I only have Linux on my computers because my friends have me do it.


FroogleDoop, we all use Linux because we choose to do so. From what I can see you have two options: 1. If you want to continue using Linux (Ubuntu in particular) you should invest some time learning all you can about your OS. This forum is a great place to start, for even if you don't have a problem there is a wealth of information about Ubuntu and how to solve problems here. Here are a couple links that can help: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  download a free Ubuntu pocket guide 

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) & 

[http://www.stchman.com/](http://www.stchman.com/)

2. I really say this after a lot of contemplation, but if you really don't want to use Linux and only do so because of your friends it may be better for you to go back to whatever you were using prior. I say this because from what you typed in this thread it seems to me that you really don't use Linux because you want to. 

If you decide to use Linux then make yourself a home in here and at your speed learn all you can. That's how I am learning.

---

