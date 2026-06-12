---
title: "Youtube sound works, but no video."
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Dark006 on 2011-03-16
Ok I've searched around for a bit and couldn't find anything to help me with this issue. Videos work on other websites, even youtube videos themselves, just not on youtube.com. The sound will work but no video is displayed, and for some reason my mouse cursor turns black. I've tried things like uninstalling the free plugins and installing the adobe one but still no luck. Any ideas? Oh, forgot to mention what version I'm running. I reformatted and started with Ubuntu 9.04 and upgraded to 10.04 (it won't let me upgrade to 10.10 for some reason). Should I just re-install the OS again?


Also, when you watch videos online are they still buffered (is that the correct term?) into the /tmp/ directory?

---

### Post by Dark006 on 2011-03-16
Anyone?

---

### Post by PunkLV on 2011-03-16
This is obviously a flash problem.
Post your browser, it's version at least.
And have you installed any video drivers lately, and what errors you get when trying to do:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dark006 on 2011-03-17
Google Chrome Stable, version 10.0.648.134. When I update also it  says "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by ivanovnegro on 2011-03-17
It seems to be really a Flash issue, what version of Flash are you using?

---

### Post by Dark006 on 2011-03-17
> **ivanovnegro said:**
> It seems to be really a Flash issue, what version of Flash are you using?

How do I check that?

---

### Post by ivanovnegro on 2011-03-17
> **Dark006 said:**
> How do I check that?

Oh, lets see, Im not sure if there is a command for the terminal to be more fast but you could go to the video from youtube and with a right click on it see what version of Flash you have installed.
10.2 has some problems that I have also, I have colored videos but the embedded ones are working.

---

### Post by Dark006 on 2011-03-17
Ok yeah I have 10.2.154.25 installed.

---

### Post by ivanovnegro on 2011-03-17
> **Dark006 said:**
> Ok yeah I have 10.2.154.25 installed.

Yes, it is actually the problematic one even on Windows and Mac.
I always said Flash is a buggy thing. :p
There are some how to's, some people are saying try the newer version, its beta 10.3 or revert back to 10.1 (I think it was that one) that worked well on 10.10.

---

### Post by Dark006 on 2011-03-17
How can I revert back? I'm not very familiar with flash.

---

### Post by ivanovnegro on 2011-03-17
> **Dark006 said:**
> How can I revert back? I'm not very familiar with flash.

Hm, revert back on Ubuntu, Im not sure how to do it as Im not on a Ubuntu machine right now. Maybe someone could join us to help.
For the beta, what of course could be unstable, I think there is a PPA.
But I have to admit Im neither a fan of Flash nor Im too familiar with it.

---

### Post by PunkLV on 2011-03-17
Hold it right there, sir.
Please do check the [http://debian-multimedia.org/](http://debian-multimedia.org/) site and its FAQ section and:
```
sudo apt get install linux-headers-`uname -r`
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
You probably will have to reboot after this. Something is obviously wrong with the packages you have installed. 

Prior to that, you can go to the address in Chrome ```
about:plugins
```and check if the adobe flashplayer is actually listed there.

---

### Post by Dark006 on 2011-03-17
@PunkLV No luck, do you guys think I should just reinstall Ubuntu?

---

### Post by ivanovnegro on 2011-03-17
> **PunkLV said:**
> Hold it right there, sir.
Please do check the [http://debian-multimedia.org/](http://debian-multimedia.org/) site and its FAQ section and:
```
sudo apt get install linux-headers-`uname -r`
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
You probably will have to reboot after this. Something is obviously wrong with the packages you have installed. 

Prior to that, you can go to the address in Chrome ```
about:plugins
```and check if the adobe flashplayer is actually listed there.

> **Dark006 said:**
> @PunkLV No luck, do you guys think I should just reinstall Ubuntu?

@Punk: I dont know if you have or dont have issues but its known that the updated Flash is not working well for all, I just tried to give some possibilities.

@Dark: I dont think that you have false packages and reinstalling would not change your situation in my opinion. Maybe what you really have to do is to try a solution, so I would say before doing anything try to search through the forums for a similar problem, that could help you.
Reinstalling has no sense, for everything there is a solution, normally. :p Thats, why we use Linux.

---

### Post by Ditchdoc7893 on 2011-03-17
Dark, this may sound dumb, as these other folks seem to have more technical answers, but have you tried opening youtube videos in Firefox?  I'm running Firefox version 3.6.15 and Flash version 10.2.152.27 and I've been watching lots of youtube videos over the last couple days without any problems.  In lieu of trying to reinstall the entire OS and everything else, I might at least give it a shot and see if you have any luck.  Best luck to you!

Ryan

---

### Post by PunkLV on 2011-03-17
@ivanovnegro
In the past I've had severe issues with flash every time I've installed/upgraded Ubuntu. And to harden things up I use only Opera. You may want to check my older threads.
So fas I've found only one way of solving flash problems: total and complete up to date installation, latest stable Opera version, manual flash install and Opera configuration. 
There probably is another way as well, but this works for me just fine.

---

### Post by Ditchdoc7893 on 2011-03-17
Punk, I haven't checked out Opera, but I will, and will probably check your threads out as well to see if I can learn something.  As far as the browser itself goes, I've been using Firefox solely since I migrated to Ubuntu and have been very impressed with its performance for all the things I do (browsing, videos, music, other media, etc.).  On that note my migration from the dark side has been very seamless.  I tried Chrome a couple times but had mixed results, got pissed off with it when I couldn't get it to do what I wanted and then went back to Firefox.  A lot of the corporate sites I have to access daily are only formatted for either IE 8.0 or greater or Firefox.  That limits me to some degree.  I, myself, will probably do some research into Opera.  I like your ideas.

---

### Post by ivanovnegro on 2011-03-18
> **PunkLV said:**
> @ivanovnegro
In the past I've had severe issues with flash every time I've installed/upgraded Ubuntu. And to harden things up I use only Opera. You may want to check my older threads.
So fas I've found only one way of solving flash problems: total and complete up to date installation, latest stable Opera version, manual flash install and Opera configuration. 
There probably is another way as well, but this works for me just fine.

Maybe I have to give Opera a try, do you think it can handle Flash a bit better as Chromium? Firefox, Im not using it quiet a long time.

---

### Post by Dark006 on 2011-03-18
> **Ditchdoc7893 said:**
> Dark, this may sound dumb, as these other folks seem to have more technical answers, but have you tried opening youtube videos in Firefox?  I'm running Firefox version 3.6.15 and Flash version 10.2.152.27 and I've been watching lots of youtube videos over the last couple days without any problems.  In lieu of trying to reinstall the entire OS and everything else, I might at least give it a shot and see if you have any luck.  Best luck to you!

Ryan

Yeah I've tried Firefox also with no luck. I haven't tried Opera though, I'll try that when I get home.

---

### Post by Dark006 on 2011-03-19
Ok so I've tried installing older versions of flash, but now I don't know where to put the files. In older versions it says that libflashplayer.so (I think that was its name) is under .mozilla/plugins. I have no plugins folder in .mozilla though. Is there an easy to to install these? It seems like this would be simple, and for me its not grrr.

---

### Post by Muster Mark on 2011-03-19
this might sound really silly, but have you tried something as simple as refreshing?  I have gotten the same issue many times, and refreshing has cleared it up for me.  although I am on 10.10

---

### Post by adduds on 2011-03-19
my only suggestion to give that fixed my problem super easily was use firefox (as it uses less memory anyways and is only slightly slower....although the 4rc is wicked fast!) and install flash aid 

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

that's how i got to 10.3 

i checked around a bit for chrome add on for flash aid...but i couldn't find one

hope that helps....don't re-install lol

---

