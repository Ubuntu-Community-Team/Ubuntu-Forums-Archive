---
title: "Graphics Media Accelerator 950  and jaunty,big problems!"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Sergio7676 on 2009-05-06
Hello everyone!

I have been using 8.10 until a few weeks ago and everything was working fine. Since I installed Jaunty I have problems of graphic performance ( I cannot play youtube full screens videos, compiz problems,etc).
I have been trying different solutions, like updating the linux Kernel but nothing worked...
I have heard that an update is to be expected to fix the problem... Has anybody found any solution?,Has anybody heard about the release of the update?

Thanks in advance!!
:)

---

### Post by Mortus Pryde on 2009-05-06
The first thing the more experianced guys are going to ask is what your graphics card is. They may then ask if you installed the restricted/proprietary drivers.

If it is ATI or Intel there seems to be bugs with these graphics systems. Some ATI cards are no longer supported under the newest Catalyst driver and there is a serious performance bug with the open source driver at current. I am not sure the details on the intel issue however.

---

### Post by Sergio7676 on 2009-05-06
My graphic car is an Intel Graphics Media Accelerator 950. It worked fine with 8.10 with "free source" drivers.


:popcorn:

---

### Post by studiodude on 2009-05-06
I think you will find the answer in this thread - it worked for me on my similar Graphics Media Accelerator.......... just follow the instructions on the link that appears on the second page.

[http://ubuntuforums.org/showthread.php?t=1136256]("http://ubuntuforums.org/showthread.php?t=1136256")

9.04 screwed up all my graphics functions after upgrading from 8.10 but this set it all straight again.

Hope it works for you.

M

---

### Post by Sergio7676 on 2009-05-07
I have tried that solution before but it did not work :( ... I tried to update the kernel too but it did not work either. May be the only solution
is to wait for an update...

Regards

---

### Post by skymera on 2009-05-07
This should fix it:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Sergio7676 on 2009-05-07
Skymera as a beginner I'm afraid your solution is too difficult for me.Besides I tried to find more information about my graphic card, I used
the lspci in the Terminal and I got:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

In the same link that you gave me I found this:

VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	

No improvement (after your proposed solution)
	

ryantm (user)
	

Continued constant high CPU, no noticeable improvements. glxgears below 30 fps, GLXgears reports GEM could not be started reverting to Classic Mode Ubuntu 9.04, kernel: 2.6.28-11. 

I begining to feel quite desperate, may be it would be a good idea to reinstall 8.10....

---

### Post by scottcrumpler on 2009-05-07
I have Intel GM 950, and after upgrading to Jaunty 9.04, I can't use any of the visual effects.  I've tried everything suggested on the forums, including the above-- (rolling back the driver to 2.4), and it had no effect.  

I'm sticking with Jaunty, because the performance is so much better, even if I can't have the visual bells and whistles for now.  But, I hope a fix is in the works for this problem!


Cheers,

Scott

---

### Post by Sergio7676 on 2009-05-07
I hope so too!!

Cheers

Sergio

---

### Post by Sergio7676 on 2009-05-08
After following this instructions I got a slight improvement. Besides, I can
play youtube videos full screen. (This instructions aim the reinstall of an older driver for the graphic card).

Go to a terminal and type:

gksudo gedit /etc/apt/sources.list

and add the following lines to the file:

deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

Save it, and close the window. Next type:

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

You may get a warning, but you should ignore that.
Martijn Bastiaan said on 2009-04-28:

Oh, and restart Ubuntu.

[https://answers.launchpad.net/ubuntu/+question/68800](https://answers.launchpad.net/ubuntu/+question/68800)

---

### Post by Sergio7676 on 2009-05-09
Sorry, I meant I can't play youtube fullscreen videos.
If anyone has any more ideas, please post.

Regards everyone

---

### Post by wamai on 2009-05-09
i can play you tube videos didn't have problem wit that but wit compiz and other desktop effect try this

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

it helped me!!

---

### Post by Sergio7676 on 2009-05-09
Thank you for you response Wamai. Although Compiz effects were working ok I have tried your suggestion. I am afraid, I still have the issue with the youtube full screen videos :(!

---

### Post by scottcrumpler on 2009-05-10
Wamai -

Thanks for the suggestion.  I tried that command line you suggested in order to get the visual effects working, and it totally blanked the screen when I tried enabling visual effects.  I was able to get it back to normal by alt-tabbing to the right window and hitting ESC.  

Will just have to wait for a fix from Ubuntu. 

-Scott

---

