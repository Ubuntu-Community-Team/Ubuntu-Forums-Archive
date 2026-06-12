---
title: "Colors are all wrong when playing videos"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Timzor on 2009-02-20
Since the day before yesterday, all the characters in any video I watch are suddenly blue.  Observe.
[IMG]http://img.photobucket.com/albums/v221/IronMagus/Screenshot-2.png[/IMG]
This happens regardless of media player (VLC, movie player) and video format (DVD, mp4, etc.).
However, if I boot into Vista, the videos play just fine.
As cool as it is to have every anime I play look like Interstella 5555, I'd really like to figure this out.  Please help, I'm completely at a loss.

Worth mentioning that I'm very inexperienced with Linux/Ubuntu, so please dumb things down as much as possible.

---

### Post by lukjad on 2009-02-20
Open up totem (*Applications->Sound and Video->Movie Player*). Click *Edit->Preferences* and choose the *Display* tab. Near the bottom right hand corner there should be a button that says *Restore To Defaults*. Click that then click *Close*. That should fix it.

EDIT, if that doesn't work, you may wish to try a few other things. I'll post them if you need them.

---

### Post by Timzor on 2009-02-20
Unfortunately, everyone's still blue.
As I said, it's the same story regardless of which program I use to play the movies.

---

### Post by lukjad on 2009-02-20
Okay, I found this [link]("https://answers.launchpad.net/ubuntu/+source/totem/+question/7373") that seems to be the solution. Please note that I haven't tested this so I cannot be sure it will work.

Open the terminal (*Applications-Accessories-Terminal*) and type:

```
gstreamer-properties
```

A box should pop up called **Multimedia System Selector**. Choose the *Video* tab. Under the heading **Default Output** it most likely will say Autodetect. Change that to **Custom**. In the Pipeline input box paste this:

```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```

That should do it.

PS, if it does, please tell me. I really want to know.

---

### Post by Timzor on 2009-02-20
Unfortunately, it didn't work at all.

Should I change it back?

*edit*
Okay, I looked around in that thread you linked me to, and found another suggestion if the first didn't work:
videobalance hue=-1 ! autovideosink
in the custom line.  That did the trick!

Thanks for your help.

I think there's a thank feature on this site... if you tell me how to do it, I'd be glad to give you one.  XP

---

### Post by lukjad on 2009-02-20
Well, try a reboot, just to see if that is what is needed for it to take effect. If it does nothing, then reset it back to what it was before.

I'll see if I can dig anything else up.

---

### Post by faind on 2009-02-22
what you have to do is really simple, it seems that the problem is with the nvidia drivers , go to System>Administration>Nvidia X Server Settings 

Locate XVideo XServer settings and turn the hue bar all the way down to zero 
:KS

---

### Post by lukjad on 2009-02-23
> **Timzor said:**
> *edit*
Okay, I looked around in that thread you linked me to, and found another suggestion if the first didn't work:
videobalance hue=-1 ! autovideosink
in the custom line.  That did the trick!

Thanks for your help.

I think there's a thank feature on this site... if you tell me how to do it, I'd be glad to give you one.  XP
There is one, but it's currently disabled because the server is having trouble. It should come back some day, but who knows when. Don't worry about it though, your personal thanks is more than enough. :D

---

### Post by marcelofontenele on 2009-03-14
Hi

I had the same problem here and after some research i found one solution (at least for me :-) )

Do the following:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

**videobalance hue=-1 ! autovideosink**

Good luck :P

Marcelo Fontenele
From Brazil

---

### Post by mohammadul on 2010-06-30
:guitar:OK! For me, I had to do the following:

1) Open Terminal.
2) Type [COLOR=Red]gstreamer-properties[COLOR=Black].
3) [COLOR=Navy]Multimedia Systems Selector[/COLOR] opens up.
4) Go to Video Tab.
5) [COLOR=DarkRed]X-window System (No xv[/COLOR]).
[/COLOR][/COLOR]

---

### Post by cmccauley on 2011-03-30
I tried what mohammadul suggested and it Works!


1) Open Terminal.
2) Type gstreamer-properties.
3) Multimedia Systems Selector opens up.
4) Go to Video Tab.
5) X-window System (No xv).


Thanks mohammadul

---

### Post by Predrag Jelic on 2011-05-03
> **mohammadul said:**
> :guitar:OK! For me, I had to do the following:

1) Open Terminal.
2) Type [COLOR=Red]gstreamer-properties[COLOR=Black].
3) [COLOR=Navy]Multimedia Systems Selector[/COLOR] opens up.
4) Go to Video Tab.
5) [COLOR=DarkRed]X-window System (No xv[/COLOR]).
[/COLOR][/COLOR]


This worked for me! Many thanks! :-)

---

### Post by Pithikos on 2011-08-29
That didn't work for me. I just launched the the nVidia-Settings and switched everything to default and it worked(everything was working before some updating).

---

### Post by Claus7 on 2011-11-24
Hello,

> **mohammadul said:**
> :guitar:OK! For me, I had to do the following:

1) Open Terminal.
2) Type [COLOR=Red]gstreamer-properties[COLOR=Black].
3) [COLOR=Navy]Multimedia Systems Selector[/COLOR] opens up.
4) Go to Video Tab.
5) [COLOR=DarkRed]X-window System (No xv[/COLOR]).
[/COLOR][/COLOR]

ati card, some latest updates for xorg and new kernel for maverick. Doing this solution, movie player was fixed right away. After rebooting all the players did the job. The colours were...greenish-red. Not blue in my case.

edit2: after some reboots, things are back to normal, reversing the aforementioned solution... odd that is...

Thanks,
Regards!

---

