---
title: "No sound in speakers but sound in headphones"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by rohit.rohan09 on 2010-08-18
Hello People,
Please help me out.. I am in a big fix!!

I had installed Ubuntu 9.10 some days ago and was very happy to get rid of Windows once and for all.. Only then I upgraded online to 10.04 and the problem started..

I did not get sound from my laptop speakers but only from the headphones on plugging them in.. i tried thousands of suggestions and modifications.. downloaded and installed umpteen things.. but nothing worked to change..

Now I have removed 10.04 and reinstalled 9.10 in a bid to revert to my previous settings.. but nothing worked! Infact I still have the same problem and it is very irritating..

I am new to Ubuntu and was mighty impressed.. however now Windows now seems to be the only resort left for me to be able to hear my laptop again..

Please help me.. I do not want to switch back to Windows once more!!

---

### Post by Ampi on 2010-08-18
The thing is, I had the same problem after installing 10.04, but I don't remember well the fix. My fix was simply somewhere in some advanced audio settings, unchecking a mute preference. Some kind of bug. 
I do remember that finding the solution was very easy in google, so I m guessing that must not be your problem. Anyway, in some vain effort, here is the link to the most common audio problems.

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Maybe someone else can help you if you post some more details... Im to much of a rookie to help you yet..

P.S. Please don't switch back to Windows, like they say in Holland, all beginning is difficult! I switched 5 years ago... Still going happy with the occasional frustration that does NOT compare to the continuous frustration of Windows...

---

### Post by Braik on 2010-08-18
Hi, I have two different proposals for your problem:
 
1. Since you seem to have sound from your headphones, it means that the solution proposed by Ampi should be the good, the drivers and sound card working. Now if you tried to go back to Karmic (9.10) and your sound crashed I think you messed up the drivers, so you should try to fix that up by checking "alsa"-related packages, or try the second solution as well.
 
2. Since your installation seems quite new, why you don't try to make a new proper Lucid (10.04) installation ? I propose you that because once I had a graphic card issue when (on-line) upgrading from Karmic to Lucid, that was repaired by a clean new installation of Lucid. Before you do that you should maybe backup your home folder, and even putting it on a separate partition that gives you a better data protection.
 
Good luck

---

### Post by rohit.rohan09 on 2010-08-18
Thank you for the response..
However, I have tried everything in the system.. everything seems to be working fine n ready according to the volume controls too.. but the sound comes out only from the plugged headphones..
And I have also gon through each of the suggested measures of the link to the common ausio issues.. nothing worked for me! 

Also, I have already done a clean install of 9.10 once just yesterday.. should I like format the enitre hard-drive and install unbuntu once again??

---

### Post by Ampi on 2010-08-18
Hmm, difficult. 


I guess you already checked the gnome-volume settings, I´m just trying to make sure you tried everything, sorry if it´s a repeat for you..

run gnome-volume-control 
go to Switches tab
check/uncheck speaker and headphones

In case you have an intel sound card check the alsa settings like Braik suggests. You can do this with

```
sudo gedit /etc/modprobe.d/alsa-base
```

At the end check what it says in that file should be something like, only in case of an intel card!

```
options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic
```


If you run aplay -l you can see what your audio device is..

---

### Post by rosehipzero on 2010-08-18
Did you try using Pulseaudio? Maybe that'll fix it.. MAYBE

---

### Post by rohit.rohan09 on 2010-08-19
Edited the alsa-base.conf file earlier as well as again.. no use..
Also.. I have PulseAudio installed..
:mad:

---

### Post by bee410 on 2010-08-21
I also had this problem, I solved it once, then had to reinstall ubuntu and had to start all over again...
But this is what definitely helped this time: I upgraded to Alsa 1.0.23 as described here:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

After that, I had sound on speakers AND headphones - at the same time :-) Haven't figured out yet how to make speakers stop automatically when I plug in the headphones, but I can do it manually with Alsa Mixer (which I also installed, through the package manager): Turn down the "Front" option to minimum. ("Mute" doesn't work, it just mutes the headphones again.)

---

