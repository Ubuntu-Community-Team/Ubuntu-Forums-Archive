---
title: "youtube"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by ECET on 2010-06-28
Hello all.....I have tried to watch some videos on you tube but for some reason I can't. I'm running Ubuntu 10.4.....and I believe I've missed something in settings somewhere that will allow me to do this. I can watch downloaded movies....I can watch some of the "bad variety" type movies.....but no you tube. Can you tell me what I have missed please?.....thanks

---

### Post by TeoBigusGeekus on 2010-06-28
Have you installed the flash plugin?

---

### Post by nhasian on 2010-06-28
to add flash, click [here]("apt:flashplugin-nonfree")

after installation is complete, restart your firefox browser.

---

### Post by ECET on 2010-06-28
thanks....I am still at work...but when I get home I will definatly check and see......thank you!!......I'll post later and let cha know if its fixed.....):P

---

### Post by TeoBigusGeekus on 2010-06-28
Also, some more info about your avatar!

---

### Post by ECET on 2010-06-28
I found that online under ubuntu desktop/wallpaper....but......I have just been asked to change it......

---

### Post by TeoBigusGeekus on 2010-06-28
Damn you mods!!!

---

### Post by overdrank on 2010-06-28
> **TeoBigusGeekus said:**
> Damn you mods!!!

:confused:

---

### Post by TeoBigusGeekus on 2010-06-28
> **overdrank said:**
> :confused:
There should be a nsfw thread... you know... for relaxation...:lolflag:

---

### Post by ECET on 2010-06-28
ok....I tried the flash install....you tube still not playing videos.....what else can i try????

---

### Post by TeoBigusGeekus on 2010-06-28
Which browser do you use?

---

### Post by Yarui on 2010-06-28
If you already installed flash and it didn't help this probably won't make a difference, but I like to install the ubuntu-restricted-extras package.  It contains flash, java, some multimedia codecs and various other useful plugins.

---

### Post by ECET on 2010-06-28
firefox.....sorry....should have said so earlier.....I'm a bit slow these days!!!!

---

### Post by TeoBigusGeekus on 2010-06-28
Well... have you installed the restricted extras?

---

### Post by ECET on 2010-06-28
not sure.....please explain what I might need to do and I'll see if it rings a bell.....I had an instructor at school help me out with some things and he may or may not have done this....I can tell you I have installed the animation extras...and I got wireless internet to work by having ubuntu look at and download drivers.......

---

### Post by TeoBigusGeekus on 2010-06-28
Open terminal and give
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ECET on 2010-06-28
I have already done this according to the output on terminal:

eading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



ok....so now I guess its getting tricky......any other ideas....I hope!!!!

---

### Post by TeoBigusGeekus on 2010-06-28
1)Try with a different browser.
2)Empty firefox cache and try again.
3)???
Run out of ideas, sorry...

---

### Post by ECET on 2010-06-28
ok....thanks.....I'll do that then read some more of this book I bought: tips, tricks,hacks for Ubuntu

---

### Post by Yarui on 2010-06-28
Have you tried checking your browser plugins for flash?  Even if it is installed I suppose it is possible that it didn't end up getting properly added to your Firefox plugins.  If you open Firefox and go to [ Tools > Add-ons > Plugins ] you should find an entry labeled "Shockwave Flash".

---

### Post by gandaran on 2010-06-28
ECET
what version of ubuntu do you have? 10.04 or an older version? and 32-bits or 64-bits?

---

### Post by ECET on 2010-06-28
10.04....64 bit

---

### Post by nhasian on 2010-06-29
no ones mentioned this, but in firefox for the url type:

```
about:plugins
```

does yours show flash is installed??  on my ubuntu 64 bit it says:

> Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

---

### Post by ECET on 2010-06-29
I'm once again back at work and without my laptop....I know I have shockwave installed but have not looked in the firefox browser to see if its there. I will once again look and get back later when I get off work. Thanks for all the help.....by the way, I installed the google/chrome you tube add-on.....and I still cant get the videos to play.....I inserted the address.....it shows the thumbnail of video I want to play, but when I press on thumbnail to play.....it does nothing......I obviously have a setting wrong or something simple I'll bet, just not sure where to look or go......again, thanks and I'll get back later and see......):P

---

### Post by Yarui on 2010-06-30
Do you, by chance, have something blocking javascript?

---

### Post by ECET on 2010-06-30
I do not know....how would I check?

---

### Post by Yarui on 2010-06-30
Well I don't think a youtube video player will appear at all if you have javascript entirely disabled, but just to be sure you can go to "Edit > Preferences > Content" in Firefox and make sure the "Enable JavaScript" box is checked.

If you don't already know whether or not javascript is blocked I think it's safe to assume you don't use any javascript blocking plugins, so if you have javascript enable that probably means javascript isn't part of your problem.

---

### Post by ECET on 2010-06-30
Thanks...when I get home, I'll take a look at this...thanks):P

---

### Post by ECET on 2010-07-01
well,.......I can watch you tube now....but I had to install another add on in Firefox....can't remember right off the top of my head what its called, but it was something that allowed me to add face-book, linked In and you-tube all into this software. It would even let you link into instant messenger, and about 2 or 3 other apps......So....while I cant go to you-tube directly in my browser the way I used to.....I can however go into this add on and watch some clips....so thanks to all of you who offered advice......I'm working now and quite happy about it........I'm getting closer to cutting the umbilical from ole' MS!!!!!:D

---

### Post by ECET on 2010-07-01
OK folks.....I promised I would let you know how I got my you tube to work....its an add on in firefox called "Yoono".....it allows facebook, and the others I listed earlier to work through it. Its very acceptable and once again I would like to thank everyone who has gave me valuable input.....I'm not sure how to mark this as solved, but my issue has been solved......

---

### Post by Yarui on 2010-07-03
It's good that you got youtube working but a bit of a shame that you didn't figure out what is keeping it from working normally.  If you are lucky a future update may make it work with no work at all, which wouldn't normally be an acceptable solution, but since you are satisfied with your current solution it shouldn't be difficult to hold out for a future update.

Anyway, congrats on your success.

---

