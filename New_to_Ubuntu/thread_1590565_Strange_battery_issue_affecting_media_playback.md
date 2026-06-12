---
title: "Strange battery issue affecting media playback"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by zerojoy on 2010-10-08
I have a strange issue with ubuntu lately. I have my music, video, and flash playback all playing very choppy and randomly cutting out at any given time when my computer is running on battery power.

Everything plays fine until I disconnect the power cord and run on the battery power. I have tested this a lot, I thought it may be pulseaudio since at startup it has a high priority for some reason, you can see it running at -11 under the nice section.

I have never had this problem with any version of ubuntu until 10.04.1. Any version I drop down to doesn't do this to me, just 10.04.1 and above.

I am running 10.10 i386 desktop edition right now and using an eee pc 1000HE netbook. 

I will say that everything is fine, video, sound and flash alike play perfect with anything running in the background and ram full, just not when disconnected from the power cord.

Is anyone else going through this? I love ubuntu and I want to be able to make my netbook work disconnected.

---

### Post by zerojoy on 2010-10-09
Well, now its happening even when connected. I did try another linux distro, I used fedora and had no issues such as this. Just ubuntu. 

I did a full reinstall of 10.04.1 and had no issues until updating software with the software manager.

Seems to me that it may be poor memory management somewhere in the recent updates.

It can't just be me with these problems, is it?

---

### Post by P4man on 2010-10-09
HAve a look at the cpu frequency scaling applet (add it to your panel). Im guessing its running at the lowest available speed?

---

### Post by zerojoy on 2010-10-09
I have that added and I have tried making it hit the lowest possible, I have it set for 1ghz and it still does it.

I have noticed that it does spike a lot and hit 1.67 for no real reason. Just does it on its own. I have never really set it to 1ghz or 1.33 ghz until the last few days just to see if its because the processor is too bogged down with it hitting 1.67 too often.

still not sure what could be doing it.

---

### Post by P4man on 2010-10-09
Open a terminal and run "top" and see if anything is hogging your cpu. YOu can also use "system monitor", but its a bit less accurate. Make sure to look at *all* processes in the view menu and not just your own. See if anything is using abnormal amounts of cpu times or memory.

---

### Post by zerojoy on 2010-10-09
I used top and I saw a process that spikes when it makes the music or video skip. some process called "phy0". Ir doesn't become a high process, it goes upto 8 or something like that. But, every time it turns  on or it is visible in top it makes the music and video skip and chop. 

So I think I have found the problem, but I have never heard of the process "phy0" and I have been looking online all over to figure out what it is but I can't find any info. 

I could be wrong, it could be a combination of things but I am not sure. The other part is, it doesn't appear all the time. I see it creep up the line to the 2nd to the top inside "top" and when it hits the second line, the media skips

PID 638, USER Root, PR 20, NI 0, VIRT 0, RES 0, SHR 0, S S, %CPU 8, %MEM 0, COMMAND phy0

sorry if I didn't write that properly, I copied it out of top the best I could.

---

### Post by zerojoy on 2010-10-12
It's still doing it, but now it is called phy1. I have no idea what this process is and it randomly goes the the top of the list within "top" and makes my media skip and now noticing that it stops all processes for a split second and I can't even move the mouse. 

does anyone know what phy0 and phy1 is????????

---

### Post by Matt__ on 2010-10-12
> **zerojoy said:**
> 
does anyone know what phy0 and phy1 is????????

only time Ive come acros those is with regard to Atheros wireless drivers and [noise floor calibration timeout](https://lists.ubuntu.com/archives/kernel-bugs/2009-March/049084.html) that locks up system response due to cpu hogging. [more here on it](http://www.spinics.net/lists/linux-wireless/msg57415.html)

cant say I really know anything about it, but as you have no other avenues of exploration I thought I would mention it.

---

### Post by zerojoy on 2010-10-12
Thanks Matt. I was looking in that direction. Its strange that my wifi driver would be doing that. It was fine back when 10.04 was first released and all before it. I wonder what changed.

I did a test, I turned my wifi off and no LAN and I did notice that there was no issue with any media cutting out or any trace of phy0 or phy1. No matter how hard I taxed my machine, everything played fine and no slow downs with other programs. 

Seems like a bug that needs fixing. 

So, right now I am looking for another driver for my atheros wifi and wondering if going the ndiswrapper is wise. 

anything to get rid of this issue.

---

