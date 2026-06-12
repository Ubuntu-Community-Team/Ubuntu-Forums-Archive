---
title: "Flash Problems?!?!!?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Pw00t on 2010-11-09
Hello all,
First time Linux user here, installed ubuntu on my laptop a few months ago. Its been fantastic up until now, really love the OS. I have been experiencing some difficulties, however, with flash videos like youtube in firefox. These problems have just started up over the last few days. Before that flash video worked fine. When it does work the audio is fine but the video is all choppy and sometimes it wont display anything at all. I've tried setting my visual effects to none but that had no appreciable effect. I've also tried using other web browsers (google chrome) and reinstalling both adobe flash player and firefox, also with no luck.

Please help meeeee!

---

### Post by wiseguy12851 on 2010-11-10
I am not quite having the exact same problems but close to yours, mine to started up over the past few days, in fact, as I type I'm loading VMware with another operating system that currently plays it correctly.

The problems I'm having are weird and don't initially seem to be connected to each other:

[LIST]
[*]Certain flash-based applications don't load at all or are always loading and never play. These include flash-based message boards and flash-based players
[*]For each flash-based application/player that doesn't load at all they all show different error messages in very different ways, it almost looks like it's programmed wrong
[*]For each flash-based application/player that does load and that does play it appears to play but over 2kb/s dial up Internet. It buffers at normal pace but it's acting like nothings being buffered even though you can see it has, it's always re-buffering every 500 - 2000 ms
[/LIST]
The only flash player I have seen that works for me is MegaVideo, with it's odd rebuffering. Everything else either doesn't load with or without an error message or never stops loading

---

### Post by Rubi1200 on 2010-11-10
Check out the possible causes and solutions here:
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

### Post by ubudog on 2010-11-10
Try this command in a terminal.  (It installs a bunch of codecs and flash related things)

```
sudo apt-get install ubuntu-restricted-extras
```

You may want to run it before you go to sleep, because it can take a while on a slow internet connection.

---

### Post by wiseguy12851 on 2010-11-10
I'll try those things but I don't have slow Internet connection but high-speed cable, What I meant was MegaVideo buffers normally (with high-speed connection) but plays the video as if I'm on the slowest dial-up Internet in the world, thus far MegaVideo is the only place I've seen that can play anything.

---

### Post by wiseguy12851 on 2010-11-10
It still didn't fix the problem however the other browser, Google chrome, now fully works with flash. nothings changed in firefox...

---

### Post by Rubi1200 on 2010-11-10
On the same site I linked to before:
[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

Just make sure you have a backup of your profile first please.

---

### Post by ubudog on 2010-11-10
Also, are you using the latest version of Firefox?  You can check in Help>About Mozilla Firefox.  It should say 3.6.12.  If not, you can use update-manager to install the latest. :)

---

### Post by TBABill on 2010-11-10
You also did not state which version of Ubuntu you are using (10.10, 10.04, 9.10, etc). Firefox relies on a user-installed version of flash. Chrome and Chromium do not...they have it installed within the program. So it makes sense that Chromium would work and Firefox may not. Lovinglinux created a wonderful extension called "Flash-Aid" and it will take all the guess work out of keeping your flash version up to date for you. It also swaps out the 32 bit version for the 64 bit if you installed ubuntu-restricted-extras on a 64 bit machine. You could see a world of improvement just by adding it and letting it do its thing. You can find it at the links to his posts above.

---

### Post by ubudog on 2010-11-10
> **TBABill said:**
> You also did not state which version of Ubuntu you are using (10.10, 10.04, 9.10, etc). Firefox relies on a user-installed version of flash. Chrome and Chromium do not...they have it installed within the program. So it makes sense that Chromium would work and Firefox may not. Lovinglinux created a wonderful extension called "Flash-Aid" and it will take all the guess work out of keeping your flash version up to date for you. It also swaps out the 32 bit version for the 64 bit if you installed ubuntu-restricted-extras on a 64 bit machine. You could see a world of improvement just by adding it and letting it do its thing. You can find it at the links to his posts above.

Sound like a good add-on, lovinglinux is a great developer.

---

### Post by TBABill on 2010-11-10
He's a great developer and tremendously helpful on the forums. And he has other extensions that I want to look into as well.

---

### Post by ubudog on 2010-11-10
> **TBABill said:**
> He's a great developer and tremendously helpful on the forums. And he has other extensions that I want to look into as well.

Yeah, he knows pretty much everything there is to know about Firefox.

---

### Post by cutterschoice on 2010-12-07
Hey, I'm a total noob with linux and well everything else, but i'm having the same problems with my flash. I tried the flash aid and it didn't work. Just wondering if you could tell me how to enter commands, what I need to do etc. bear in mind, I have no idea what a terminal is and only a vague idea of a command.

---

### Post by ubudog on 2010-12-08
> **cutterschoice said:**
> Hey, I'm a total noob with linux and well everything else, but i'm having the same problems with my flash. I tried the flash aid and it didn't work. Just wondering if you could tell me how to enter commands, what I need to do etc. bear in mind, I have no idea what a terminal is and only a vague idea of a command.

A terminal is a place where you enter the commands.  In Ubuntu, you can open one by clicking Applications>Accessories>Terminal.  The terminal window should come up.  Now, what you want to do is install a package.  Type the following command (just type it in and press enter).  

```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password (it will be blank), and press enter.  It should then ask you to press "Y" to continue.  Press y, and it should complete the installation automatically.

---

### Post by Joliea on 2010-12-08
> **ubudog said:**
> A terminal is a place where you enter the commands.  In Ubuntu, you can open one by clicking Applications>Accessories>Terminal.  The terminal window should come up.  Now, what you want to do is install a package.  Type the following command (just type it in and press enter).  

```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password (it will be blank), and press enter.  It should then ask you to press "Y" to continue.  Press y, and it should complete the installation automatically.
It didn't work. I still can't play videos on youtube, they keep moving in blocks instead of flowing properly. the sound is there but the pictures are not moving properly, as if its got scratches or something. 

the movies are working fine in firefox its google chrome that's not functioning. i have ubuntu 10.10 64 bit and also google chrome 64 bit.

PLEASE HELP!

**update:** the videos work fine in embedded format but not on the youtube website itself.

---

### Post by ubudog on 2010-12-08
Hmm, maybe try the 64bit part of this page?

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Don't know if it will work, as I have hardly used 64bit.

---

### Post by Lordluen on 2010-12-08
I also had flash problems when I installed Ubuntu 10.10 on my 64-bit laptop. I found that the issue is that flash 9 has issues with 64-bit ubuntu. Since flash 10 has not been officially released for 64-bit linux, the default flash installed by firefox is flash 9. I recommend downloading the pre-release of flash 10 for 64-bit linux. While it has some bugs, it fixed nearly all of my problems.

---

### Post by ubudog on 2010-12-08
> **Lordluen said:**
> I also had flash problems when I installed Ubuntu 10.10 on my 64-bit laptop. I found that the issue is that flash 9 has issues with 64-bit ubuntu. Since flash 10 has not been officially released for 64-bit linux, the default flash installed by firefox is flash 9. I recommend downloading the pre-release of flash 10 for 64-bit linux. While it has some bugs, it fixed nearly all of my problems.

Hmm, thanks.  That will help a bunch of people.  :p

---

### Post by Joliea on 2010-12-09
> **ubudog said:**
> Hmm, thanks.  That will help a bunch of people.  :p
Hey!

Mine's fixed. I think the pre-release of Adobe flashplayer 64 bit worked. I just tried playing a youtube video on the website and its working perfectly. 

Thanks y'all!

---

### Post by ubudog on 2010-12-09
> **Joliea said:**
> Hey!

Mine's fixed. I think the pre-release of Adobe flashplayer 64 bit worked. I just tried playing a youtube video on the website and its working perfectly. 

Thanks y'all!

Sweet!  Glad it's fixed.  :D

---

### Post by Joliea on 2010-12-10
Oh wait, apparently it works with a selected few videos. Am thinking the heavier it is the harder it is to play properly and it only moves about in chunks though the sound is there. 
*sigh*

---

