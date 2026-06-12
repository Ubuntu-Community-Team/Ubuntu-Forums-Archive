---
title: "Just installed Ubuntu 11.04  and it's slow"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by mafaldaspeaks on 2011-06-07
I'm not a beginner in using Ubuntu but I am quite untechie.

I just gave up Windows 7 and installed Ubuntu only on my laptop. Windows 7 was running well and fast but since I'd really like to make complete switch to Ubuntu, I'm trying to do that now with 11.04.

The thing is, Ubuntu is quite slow. For instance, start up takes at least one minute (I still can't quite believe it since Win7 was faster); when I have two or three programs running, the laptop hangs/locks/stops responding.

I have 3.9g memory, Core 2 duo processsor, and 200g available disk space. Could anyone hint at what could be wrong?

---

### Post by ivanovnegro on 2011-06-07
Maybe your graphics card? Which one do you have?
Dont forget Ubuntu 11.04 is a modern OS, for me it is comparable to Windows 7 in speed/performance. 
If you want something lighter, you should change the Desktop Environment.

---

### Post by mafaldaspeaks on 2011-06-07
> **ivanovnegro said:**
> Maybe your graphics card? Which one do you have?
Dont forget Ubuntu 11.04 is a modern OS, for me it is comparable to Windows 7 in speed/performance. 
If you want something lighter, you should change the Desktop Environment.
I have nvidia GeForce 9300m GS 512mb and I used the instructions in another thread here on how to install the latest stable version. Seems to work because Unity works although I asked a question in that thread which I quote here... [http://ubuntuforums.org/showthread.php?t=1771806&page=4](http://ubuntuforums.org/showthread.php?t=1771806&page=4)

> **mafaldaspeaks said:**
> I have Nvidia GeForce 9300m GS 512mb in my Dell Inspiron laptop.

I did the above commands and restarted. I just want to ask why, when I checked "Additional Drivers" and highlighted the "Nvidia accelerated graphics driver (current version) (recommended)", it says below "Activated but not currently in use". Sorry if this sounds ignorant, but why does it say "not in use"? Isn't the graphics card always in use when the laptop is on?

I attached a screenshot of the message window.

---

### Post by ivanovnegro on 2011-06-07
For me it seems Unity needs too many resources on your machine, did you try the Classic Session from the login prompt yet, and maybe try the one without effects to compare the performance.

---

### Post by dFlyer on 2011-06-07
Something must be wrong. Startup on my 3 year old dell is 12 seconds. Programs are responsive and I find Unity very stable for a new desktop environment.

---

### Post by mafaldaspeaks on 2011-06-08
@ivanovnegro I can try this though I'd like to find out first if there's something really wrong bec I think Win7 uses more resources and yet it was faster on this laptop than Ubuntu now.

---

### Post by mafaldaspeaks on 2011-06-08
> **dFlyer said:**
> Something must be wrong. Startup on my 3 year old dell is 12 seconds. Programs are responsive and I find Unity very stable for a new desktop environment.
It bugs me too coz this laptop's only a year old and Win7 was running faster and more smoothly.

---

### Post by wildmanne39 on 2011-06-08
> **mafaldaspeaks said:**
> I'm not a beginner in using Ubuntu but I am quite untechie.

I just gave up Windows 7 and installed Ubuntu only on my laptop. Windows 7 was running well and fast but since I'd really like to make complete switch to Ubuntu, I'm trying to do that now with 11.04.

The thing is, Ubuntu is quite slow. For instance, start up takes at least one minute (I still can't quite believe it since Win7 was faster); when I have two or three programs running, the laptop hangs/locks/stops responding.

I have 3.9g memory, Core 2 duo processsor, and 200g available disk space. Could anyone hint at what could be wrong?
Hi, you should unintall the driver for your card and install the one from the additional drivers, it will say it is not in use but that is just a bug it really is in use after you activate it, you will have to go into synaptic to uninstall the one you downloaded that is most likely your problem.

---

### Post by mafaldaspeaks on 2011-06-10
> **wildmanne39 said:**
> Hi, you should unintall the driver for your card and install the one from the additional drivers, it will say it is not in use but that is just a bug it really is in use after you activate it, you will have to go into synaptic to uninstall the one you downloaded that is most likely your problem.

I have nvidia graphics and I installed it from the additional drivers. As you said, after installation a message box says it's not in use.

When I was installing 11.04 from the live cd, my internet connection was quite slow that day. Maybe this affected some installation files that were being downloaded?

---

### Post by xrhstaras on 2011-06-19
I have a pc Intel core 2 duo 3.06ghz 4gbytes ram and ubuntu is so SLOW that i cannot stand it ! 
It makes my pc looks like its ancient history! 
Are these people out of their minds ???

Hope they would do something about it cause it really sucks !!

---

### Post by Larkspur on 2011-06-19
> **mafaldaspeaks said:**
> I'm not a beginner in using Ubuntu but I am quite untechie.

I just gave up Windows 7 and installed Ubuntu only on my laptop. Windows 7 was running well and fast but since I'd really like to make complete switch to Ubuntu, I'm trying to do that now with 11.04.

The thing is, Ubuntu is quite slow. For instance, start up takes at least one minute (I still can't quite believe it since Win7 was faster); when I have two or three programs running, the laptop hangs/locks/stops responding.

I have 3.9g memory, Core 2 duo processsor, and 200g available disk space. Could anyone hint at what could be wrong?


I'd say it must be something to do with the drivers, since I'm running Unity with 2GB memory, a dual-core processor at 1.8mhz with about 50GB HD space, have five programs open, and Ubuntu's running fine (though Scale is slightly slower ever since I activated Scale Addons).  To make sure though, run top in Terminal, or check System Monitor>>Processes, see if any programs are hogging resources. 

Oh, and I wouldn't worry about the slow internet connection stopping important files from being downloaded; any that weren't would have been downloaded the next time you ran Update Manager.

---

### Post by wildmanne39 on 2011-06-19
Hi, I found this link that has helped a lot of people fix the problem, I to use these settings and it fixed the problem for me.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by mafaldaspeaks on 2011-07-09
> **ivanovnegro said:**
> For me it seems Unity needs too many resources on your machine, did you try the Classic Session from the login prompt yet, and maybe try the one without effects to compare the performance.

Classic Session is what I'm using now and not using effects but start up is still 45 seconds.

---

### Post by mafaldaspeaks on 2011-07-09
> **Larkspur said:**
> I'd say it must be something to do with the drivers, since I'm running Unity with 2GB memory, a dual-core processor at 1.8mhz with about 50GB HD space, have five programs open, and Ubuntu's running fine (though Scale is slightly slower ever since I activated Scale Addons).  To make sure though, run top in Terminal, or check System Monitor>>Processes, see if any programs are hogging resources. 

Oh, and I wouldn't worry about the slow internet connection stopping important files from being downloaded; any that weren't would have been downloaded the next time you ran Update Manager.

I checked Processes and there's an item called "firefox-bin" that uses 134.5 mb. Is that the Firefox browser?

---

### Post by mafaldaspeaks on 2011-07-09
> **wildmanne39 said:**
> Hi, you should unintall the driver for your card and install the one from the additional drivers, it will say it is not in use but that is just a bug it really is in use after you activate it, you will have to go into synaptic to uninstall the one you downloaded that is most likely your problem.

I've also done this but start up is still 45 secs. I know that's slow coz Win7 took that long too and Ubuntu 10.04 start up was really faster.

---

### Post by mafaldaspeaks on 2011-07-09
> **wildmanne39 said:**
> Hi, I found this link that has helped a lot of people fix the problem, I to use these settings and it fixed the problem for me.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

I don't want to sound negative but I did this too and startup's still the same.

---

### Post by wildmanne39 on 2011-07-09
> **mafaldaspeaks said:**
> I don't want to sound negative but I did this too and startup's still the same.
Hi, have you resolved your other problems that was listed in your first post except the boot time being slow?

---

### Post by goldshirt9 on 2011-07-09
<quoted spam removed>

unfortunately i too had this problem and could not find a cure.:(

minimum start up applications but still the black screen at start up.

But mint 11 , Elementary ( this o/s i really liked)  also took a while to start up ( both based upon natty by chance ??? ) 
i eventually returned to 10.04 and start up was faster by a lot.

A shame as i thought natty was a great usable progressive system .

---

### Post by MlDean on 2011-07-09
i am no expert , just sharing my observations ... 
 
which version of 11.04 did you install 32 or 64 bit ?
 
i have played around with several versions of Linux, i have Ubuntu 11.04 64 bit on this PC right now and it flies , some of the other installs acted like what you describe , i think some times you just don't get a good install and have to re-install it , i did this a couple of times and i wasn't connected to the Internet and both turned out good , it will update when you connect it to the Internet , the 11.04 version may be too much for your laptop , windows uses the hard drive cache and reserved ram to speed the system up, i don't think Linux uses this , you might try another version or a reinstall.

---

### Post by mafaldaspeaks on 2011-07-13
> **wildmanne39 said:**
> Hi, have you resolved your other problems that was listed in your first post except the boot time being slow?

Actually, no. When i have 2-3 programs running (and Firefox not), it still does slow down even more. Worse, when I'm using battery power, everything is incredibly slower. I'm really thinking of re-installing - is there a way to save settings and programs or I have to redo them all?

---

