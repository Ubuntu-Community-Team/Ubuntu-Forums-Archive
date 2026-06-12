---
title: "How to change sound recording from mic to stere-mix"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by d2btoo on 2011-03-15
Hello,

Just wondering how should I change sound source to **stereo-mix** from **mic** ( which is default sound source I think ) ?

In windows XP, I simply toggle from volume control ( recording properties ), here is a screen-shot : [http://i51.tinypic.com/2w5un80.jpg](http://i51.tinypic.com/2w5un80.jpg)

What to do in Ubuntu (Jaunty-9.04) ?

---

### Post by _0R10N on 2011-03-15
You can check for this configuration on the Sound preferences window. It allows you to set default inputs, outputs, volume, etc.

---

### Post by sandyd on 2011-03-15
> **d2btoo said:**
> Hello,

Just wondering how should I change sound source to **stereo-mix** from **mic** ( which is default sound source I think ) ?

In windows XP, I simply toggle from volume control ( recording properties ), here is a screen-shot : [http://i51.tinypic.com/2w5un80.jpg](http://i51.tinypic.com/2w5un80.jpg)

What to do in Ubuntu (Jaunty-9.04) ?
[[IMG]http://img833.imageshack.us/img833/1054/snapshot55.png[/IMG]](http://img833.imageshack.us/i/snapshot55.png/)

You mean this thingy, where you can change sound sources and re-route sound through different apps?

---

### Post by r-senior on 2011-03-15
Jack is great :) 

Here are a couple of screenshots of the simple solution with Sound Preferences:

On the Hardware tab you need to have the card set to duplex (in and out). Then on the input tab, the Connector drop-down gives you the option of microphone or analogue input (line-in). You adjust the input gain with the Input Volume slider.

---

### Post by d2btoo on 2011-03-16
Hello, 

Thanks for the screen-shots! 

@r-senior: I don't have that, in 9.04, It seems used in  9.10 and upper, also I don't have any line-in source atm. :cry:

@_0R10N: Please, can you give me step by step instructions, I've tried System->Control Center->Sound [sound capture] to various values, none helped, either it's mic or none!

presently it's set to pulse-audio [* pls see below *]

@sandyd: Thanks for the screen-shots, wow! so mixer is called *monitor* in linux world! Hmmm! so after poking around in various things, and googling ( now I know the term monitor ;) ) it seems I need to download various missing pulse-packages , specially the pulse-audio-volume-control, where I can seem re-route sound as you suggested, and it worked! :KS

But I still have a question:

#1) It seems when I re-route sound , it doesn't take effect immediately, I have to re-start the recording application. Is this normal behavior ?
( Also this some time crash few app like [gtk]recordmydesktop, next time it runs fine though... )

#2) Now when I use mic, I only have sound in left-Chanel, how to fix that ?

BTW what is JACK? I mean it's something like pulse?:confused:

---

### Post by sandyd on 2011-03-16
> **d2btoo said:**
> Hello, 

Thanks for the screen-shots! 

@r-senior: I don't have that, in 9.04, It seems used in  9.10 and upper, also I don't have any line-in source atm. :cry:

@_0R10N: Please, can you give me step by step instructions, I've tried System->Control Center->Sound [sound capture] to various values, none helped, either it's mic or none!

presently it's set to pulse-audio [* pls see below *]

@sandyd: Thanks for the screen-shots, wow! so mixer is called *monitor* in linux world! Hmmm! so after poking around in various things, and googling ( now I know the term monitor ;) ) it seems I need to download various missing pulse-packages , specially the pulse-audio-volume-control, where I can seem re-route sound as you suggested, and it worked! :KS

But I still have a question:

#1) It seems when I re-route sound , it doesn't take effect immediately, I have to re-start the recording application. Is this normal behavior ?
( Also this some time crash few app like [gtk]recordmydesktop, next time it runs fine though... )

#2) Now when I use mic, I only have sound in left-Chanel, how to fix that ?

BTW what is JACK? I mean it's something like pulse?:confused:
JACK is a professional audio system. I (as I have perfect hearing) cant stand the quality pulseaudio gives off, so I opted for JACK as my main audio system. Its used for audio production, remixing & such, as you can reroute sound through multiple apps (most apps can use JACK, ones that cant are routed through pulseaudio) Additionally, it has extremely low latency. Don't try it, setting it up is a pain in the butt.

Now, lemme see. I don't want to screw up my pulseaudio-jack setup, so I cant demonstrate properly, but at the tab at my screenshot (Input Devices), there should be a list of inputs. Mute the other one by clicking on the "mute audio" thingy. Or just make it the fallback.[U]
[[IMG]http://cdn.sandyd.me/img/thumbs/snapshot57.png[/IMG]]("http://cdn.sandyd.me/img/snapshot57.png")
[/U]

---

### Post by d2btoo on 2011-03-16
Hello sandyd,

Thanks for explaing JACK ! ( I'll look into it soon... ;) )

However in the meantime , I think I found the cause of  **Only Left Channel recording mic** problem.....

It's STEREO.... you see, I was experimenting with the gnome-sound-recorder , and that application is recording all the time , all sounds as stereo even if the source is mic.

Anyway, for example,  following works right **[COLOR="Red"]arecord -d 5 -f cd -c 1 foobar.wav[/COLOR]** , when source is mic.

edit: seems I've to choose one of the voice profile, then it's work correctly in gnome-sound-recorder. <<-- This problem is solved.


Q1. still stands...btw :rolleyes:

---

