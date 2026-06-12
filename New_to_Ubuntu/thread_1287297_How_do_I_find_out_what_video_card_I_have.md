---
title: "How do I find out what video card I have"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ConXtionS on 2009-10-10
Hi

to make along story short

the best resolution I seem to be able to get is 800X600 with the old nivida card I have in the computer

Is there a command so I can get the information from the nvidia card so I can get the right driver installed?

thanks again

Jim

---

### Post by RedSingularity on 2009-10-10
lspci will give you output with the wanted information.

---

### Post by jeremyswalker on 2009-10-10
Well, the following command should give you a good idea what card you have:
```
lspci | grep VGA
```

Have you tried going to "System > Administration > Hardware Drivers" to install the proprietary driver?

---

### Post by ConXtionS on 2009-10-10
Yes sir.... I "THINK" I have

there is a WIDGET that tells me RESTRICTED drivers are available

However when I DL those I get 640X480 instead of 800X600 which is even worse

One sec let me do that command and I will tell ya what it says

thanks bro

Jim

---

### Post by ConXtionS on 2009-10-10
jim@mythtv:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
jim@mythtv:~$ 



Thats what my puter says

---

### Post by jeremyswalker on 2009-10-10
Out of curiousity... When you clicked the widget to install the restricted driver, was there more than one version to select from? Your card should be using the 96.* version.

---

### Post by ConXtionS on 2009-10-10
No sir... only the 96 version is showing

I have already reinstalled ubuntu 4 times trying to figure this out... so I figured it was time to ask for help.

I do not currently have that WIDGET thing installed so I am running off the ubuntu drivers...

Would you like me to go ahead and FLOP it back in .... umm I mean let the widget install the restricted drivers?

thanks

jim

---

### Post by jeremyswalker on 2009-10-10
Well, you probably should reinstall it. Then, I would like to direct you to this tutorial: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). It is slightly outdated, but it should help you out. There is a section titled "Common Problems" that talks about low screen resolutions. 
Good luck! Keep me posted. I would be curious to know how you make out.

---

### Post by ConXtionS on 2009-10-10
Thank you SOOO much for the help

I have been searching and searching for a thread like this...

I will let ya know what I break next
....

I really appreciate your time sir...

Jim

---

### Post by jeremyswalker on 2009-10-10
It's not a problem at all. I am glad to help out. Good luck, and let me know if you need anything else.

---

### Post by ConXtionS on 2009-10-10
Just an update
 
Screen res for this is still kicking my butt...
 
reinstalling for the 6th time now
 
but I will get the xorg thing right sooner or later
 
 
thanks again man
 
Jim

---

### Post by 3rdalbum on 2009-10-10
Why don't you just make a backup of xorg.conf?

Unfortunately with those old Nvidia cards, they are supported by very old Nvidia drivers. Back in the days of the Geforce 2, everyone was expected to be able to modify an xorg.conf in order to use Linux. The old drivers have not progressed from those times.

---

### Post by ConXtionS on 2009-10-10
Solved.....
 
It was NOT the computer or the nvidia card... it was the dang monitor
 
 
[http://ubuntuforums.org/showthread.php?t=1287933](http://ubuntuforums.org/showthread.php?t=1287933)
 
Is the post that gives the best details I have.
 
thanks again for your help bros
 
Jim

---

### Post by gordintoronto on 2009-10-10
> **ConXtionS said:**
> Solved.....
 
It was NOT the computer or the nvidia card... it was the dang monitor


If you would be kind enough to mark the thread as "solved," it might help others.

---

