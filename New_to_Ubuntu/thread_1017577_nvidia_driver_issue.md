---
title: "nvidia driver issue"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by nicejobidiot08 on 2008-12-21
Ok i am a n00b to linux. and i am trying to install the right drivers for my nvidia Quadro FX 1000 card and i cant seem to find them. can someone help my dumbass out.

---

### Post by PmDematagoda on 2008-12-21
Did you try installing the drivers from System>Administration>Hardware Drivers?

---

### Post by nicejobidiot08 on 2008-12-22
yes it said there are "No porprietary drivers are in use on this system." I also have just updated to 8.04 and now i no longer have the option to connect to a wireless network.

---

### Post by Twitch6000 on 2008-12-22
Hummm... Okay three things I suggest you do and I know this might tick you off lol..

Anyways... I suggest you Get Ubuntu 8.10 and install that.

Then for your graphics drivers do if everything graphic wise seems to be working then you should not need to install a driver.

If you are getting some lag and such get envyng and it will help you out.

As for your wireless issue Ubuntu 8.10 has the latest Linux Kernal and should fix all of that :).


Now if you would like to stay with Ubuntu 8.04 tell me what Wireless driver you have and I can help you with that problem.

For the graphics driver problem in 8.04 are you getting lag while scrolling or moving around windows?

---

### Post by IamReck on 2008-12-22
Make sure you have the restricted repository enabled.

---

### Post by LtPitt on 2008-12-22
Download and use Envy

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

to install your nvidia :)

---

### Post by nicejobidiot08 on 2008-12-24
i cannot get 8.10 installed...

---

### Post by Twitch6000 on 2008-12-24
> **nicejobidiot08 said:**
> i cannot get 8.10 installed...

problem being...?

---

### Post by nicejobidiot08 on 2008-12-25
boot.img or ubuntu-8.10-desktop-i386.iso are not recognized.

---

### Post by nicejobidiot08 on 2008-12-25
i reinstalled 7.10 and my wireless works. but i have yet to get my video drivers to work.

---

### Post by Insane_Homer on 2008-12-25
Try these for your GFX

[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)

Details here
[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html)

Install Instruction here
[http://ubuntuforums.org/showthread.php?t=990978&page=4](http://ubuntuforums.org/showthread.php?t=990978&page=4)

---

### Post by Twitch6000 on 2008-12-25
> **nicejobidiot08 said:**
> boot.img or ubuntu-8.10-desktop-i386.iso are not recognized.

Okay that means you burned the cd to fast or incorrectly.

However since you have 7.10 and wireless working fine do what Insane_Homer has posted then use the upgrade option in 7.10 :).

```
 sudo apt-get dist-upgrade 
```

would be how

---

### Post by sharkster2007 on 2008-12-30
If you do manage to get 8.10 installed try this [http://ubuntuforums.org/showthread.php?t=973038]("http://ubuntuforums.org/showthread.php?t=973038") I am a noob to this way works with my Nvidia 6600GT and I have compiz functioning too, good luck ;-)

---

