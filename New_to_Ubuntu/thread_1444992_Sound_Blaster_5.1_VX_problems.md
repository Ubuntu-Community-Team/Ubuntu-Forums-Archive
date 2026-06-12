---
title: "Sound Blaster 5.1 VX problems"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-04-02
I have wasted many hours searching to find any way to get this card working with Ubuntu. Has anyone had any luck with this card? I get the most horrible scratchy noise thru the speakers but thats all. I would REALLY appreciate ANY help with this. Thanks in advance for anyone who can help :)

---

### Post by NightwishFan on 2010-04-02
Hello, cool user name.

Check the mixer settings by using this command in a terminal. See if anything looks out of place. I will do some research on this card.
```
alsamixer -c0
```


Edit: This is a known issue. Perhaps file a bug on launchpad about ALSA. I will dig a bit more, nearly every thread has no solution.
[http://ubuntuforums.org/showthread.php?t=1104738](http://ubuntuforums.org/showthread.php?t=1104738)

Double Edit: The only thing I have uncovered that was remotely useful was this:
[http://ohioloco.ubuntuforums.org/showpost.php?p=8974405&postcount=9](http://ohioloco.ubuntuforums.org/showpost.php?p=8974405&postcount=9)

Perhaps try installing alsa-firmware, however I do not think that will help. It is worth a try.
```
sudo apt-get install alsa-firmware
```

Last resort, try some of the tips here.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ThePinkWitch on 2010-04-02
> **NightwishFan said:**
> Hello, cool user name.

Check the mixer settings by using this command in a terminal. See if anything looks out of place. I will do some research on this card.
```
alsamixer -c0
```


Edit: This is a known issue. Perhaps file a bug on launchpad about ALSA. I will dig a bit more, nearly every thread has no solution.
[http://ubuntuforums.org/showthread.php?t=1104738](http://ubuntuforums.org/showthread.php?t=1104738)

Double Edit: The only thing I have uncovered that was remotely useful was this:
[http://ohioloco.ubuntuforums.org/showpost.php?p=8974405&postcount=9](http://ohioloco.ubuntuforums.org/showpost.php?p=8974405&postcount=9)

Perhaps try installing alsa-firmware, however I do not think that will help. It is worth a try.
```
sudo apt-get install alsa-firmware
```

Last resort, try some of the tips here.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Thankyou so much. I've searched everywhere there doesn't seem to be any solution. This card just seems to be an Ubuntu no no :( I'll try your suggestions and post back.

---

### Post by NightwishFan on 2010-04-02
Good luck to you. It seems like it is not going to work, but we can always try. I am assuming a bug report might give it some attention.

---

### Post by ThePinkWitch on 2010-04-02
> **NightwishFan said:**
> Good luck to you. It seems like it is not going to work, but we can always try. I am assuming a bug report might give it some attention.

Thanks, I think you're right. Creative cards are probably one of the most popular brands of sound card so I'm really surprised that I can't find any way of getting this card to work with Linux. I bought an Audigy which was supposed to work "out of the box" with ubuntu and It won't even recognise that. I've been messing with Ubuntu since February, spending hours and hours trying to sort out sound and network issues and my computer still won't auto connect to my network taking up to 10-15 mins if at all and I can't get Ubuntu to work with my sound cards so I'm almost at the point of chucking Ubuntu altogether. Thanks so much for trying to help :) Ps. Don't know how to file bug reports.

---

### Post by NightwishFan on 2010-04-02
As for Ubuntu I am hoping you will not blame us for lack of hardware support. It is really not our fault we do not get vendor support. The free software community works really hard to get support for devices when the vendors do not help us. Hopefully in the future it will work.

Also one last gasp, install this package and then reboot. This is assuming you are on Karmic, if you are on Lucid replace 'karmic' with 'lucid.
```
sudo aptitude install linux-backports-modules-alsa-karmic-generic
```



Ah, if you really intend to report a bug you need a launchpad account. After you sign in you can use this command:
```
ubuntu-bug *packagename*
```

Like:
```
ubuntu-bug alsa
```

Here is some info about that:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by ThePinkWitch on 2010-04-03
> **NightwishFan said:**
> As for Ubuntu I am hoping you will not blame us for lack of hardware support. It is really not our fault we do not get vendor support. The free software community works really hard to get support for devices when the vendors do not help us. Hopefully in the future it will work.

Also one last gasp, install this package and then reboot. This is assuming you are on Karmic, if you are on Lucid replace 'karmic' with 'lucid.
```
sudo aptitude install linux-backports-modules-alsa-karmic-generic
```



Ah, if you really intend to report a bug you need a launchpad account. After you sign in you can use this command:
```
ubuntu-bug *packagename*
```

Like:
```
ubuntu-bug alsa
```

Here is some info about that:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Thankyou so much for your help. I did all the stuff you suggested and the backports thing. I have sound now :) It comes up as an internal analogue sound card and works... so cool. I can play music now. THANKYOU. :p

---

### Post by NightwishFan on 2010-04-03
No problem, glad you got it working!

---

### Post by capraMambrica on 2010-10-08
Hey guys, I'm interested in this solution.
I have a very fresh install of 9.04 64 bit, and I'm getting the same static. 
I managed to fix it in my last install by ditching ALSA for OOS, but I wanted to see if this did actually work first.

I tried running:```
 sudo aptitude install linux-backports-modules-alsa-jaunty-generic
```
But got:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-backports-modules-alsa-jaunty-generic"
Couldn't find any package whose name or description matched "linux-backports-modules-alsa-jaunty-generic"
...
```

Is there something obvious I'm missing here? Apt-get has been working for other things :\
Thanks!

---

### Post by NightwishFan on 2010-10-08
It appears Jaunty does not have an alsa backports package. You should probably update to Karmic, Jaunty goes end of life very soon.

---

### Post by capraMambrica on 2010-10-08
Oh wow, that is very soon. I'll look at updating. Thanks!

---

