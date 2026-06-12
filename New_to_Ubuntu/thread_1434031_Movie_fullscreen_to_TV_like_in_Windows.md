---
title: "Movie fullscreen to TV like in Windows?"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by RED666 on 2010-03-19
Hi,
I just installed Ubuntu 9.10 on my box to see how I like it. If it functions ok for my needs I'll leave Ms for good!

Windows had one nice feature though (witch I waited for long enough as it is) or more exact NVidia made a nice feature in their windows driver config software, and that is:

I use a NVidea Geforce6200, in the software that you get from NVidia with the driver there is an option that if checked, when you play any video file in a window on your primary screen, it ALSO sends the picture full screen to your television (via s-video).

B.t.w. I downloaded and installed the drivers NVidia provides for Linux.

Will I have to learn to live without this luxury in my Ms free future??

Please tell me it's not so!

---

### Post by albert s on 2010-03-19
Im not sure exactly what you mean but F11 plays full screen for me
and Im using Nvidia

---

### Post by 2hot6ft2 on 2010-03-19
On my laptop Fn+F4 sends the video out to an external display by either the SVGA port or HDMI. On the desktop I use the TV as the monitor by a SVGA cable. On a VAIO Laptop I used to have I used to do out to TV with cables that were small mic like plugs on the pc end and RCA plugs on the other end.

They were, and are, full screen on the TV's. Perhaps you mean cloned which yes that worked and works too.

---

### Post by cerealtx on 2010-03-19
you could also use vlc player which i high recomend and it has full screen options as well as many other nifty things

---

### Post by xifer on 2010-03-19
I'd have expected that to work - you mentioned you installed the drivers but did you run the nvidia config for linux and enable the option?

---

### Post by myforwik on 2010-03-19
I think you guys are not understanding him.

His svideo output is full screen anytime a movie plays - even if he doesn't have that windows full screen on his main display, and even if its minimised etc. This way someone can use the PC at the same time that someone is watching a movie on the TV. I guess he just has to setup dual screens and put it full screen on one.

---

### Post by 2hot6ft2 on 2010-03-19
> **myforwik said:**
> I think you guys are not understanding him.

His svideo output is full screen anytime a movie plays - even if he doesn't have that windows full screen on his main display, and even if its minimised etc. This way someone can use the PC at the same time that someone is watching a movie on the TV. I guess he just has to setup dual screens and put it full screen on one.
I think you can do that with the Separate X Screen Configuration as shown in the screen shot below. The TV is busy right now being a monitor for the other pc and a TV right now so can't play with it to make sure.

---

### Post by RED666 on 2010-03-19
Myforwik you get it. My tv is a long way away from my pc, so it's an effortless way to start a movie. For some reason the option exists in the WinXP NVidia tool but not in the Linux version of the utility shipped with the driver. At least I couldn't find it.

Ones your used to something a certain way, it's hard to just give it up because Ubuntu is so great!

Btw I don't get the terminology in the screen configuration in Linux, what is a "separate x screen" ?

EDIT : Thanks 2hot6ft2, we crossed replies!

---

### Post by 2hot6ft2 on 2010-03-19
> **RED666 said:**
> what is a "separate x screen" ?
That would be a separate monitor, like what you're describing I believe. 2 screens showing different things like a dual monitor. Something going on 1 and something else on the other but like I said I can't play with it right now the TV is already doing double duty.

---

### Post by xifer on 2010-03-19
when you say nvidia drivers - do you mean the nvtv package ?

---

### Post by RED666 on 2010-03-19
No... Well I don't recognize the name, but since I'm such a newb that isn't saying much....

The drivers I talked about I got offered by Ubuntu  as "available hardware drivers" automaticly after starting Ubuntu the first time (or from the CD)

The tool that got installed is called:
System-->Management-->>  NVIDIA X Server Settings

Driver
"NVIDIA Graphics accelaration Driver (Vesion 185) recommended"

---

### Post by 2hot6ft2 on 2010-03-19
> **xifer said:**
> when you say nvidia drivers - do you mean the nvtv package ?
I didn't even know about that package. I installed it but I guess there has to be a TV hooked up for it to start. Something else to play with later.
;)

---

### Post by HalfEmptyHero on 2010-03-19
I don't know how to do what you are talking about, however if you want to watch a video full screen on your TV and still be able to browse the internet and what not, its not very hard. 

Under X Server Display Configuration (in Nvidia X Server Settings of course) click on your TV. If you do not see it, make sure the cables are connected and hit detect displays.

Then hit Configure... and click on TwinView and then Ok. 

Under Position, select the position of your TV. If it is the right of your monitor choose right, although anywhere will work. 

Then I suggest choose the highest resolution your tv/cable connector can do. Hit apply, and you should be good to go.

For some reason though, whenever I do this I end up getting the panels and such on the tv screen instead of the monitor. I get around this with the following:

Click on your monitor icon, and make sure 'Make this the primary display for X Screen' is checked.

Click back on the TV icon, and then make the position of the screen above. Apply, and tell the dialog you want to keep these settings.

Change the position back to the original one you had it on (it is right for me) and apply and keep the settings. (So for me, I originally had it right of screen, then put it above of screen, and then back to right of screen)

This fixed that issue with me.

Now, to view a movie on the TV, open the movie and drag to the edge of the screen where you put the TV (right for me). You will be able to drag it onto your tv. Make it full screen as you normally would, and then bring your mouse back to your monitor.

---

### Post by xifer on 2010-03-20
> **HalfEmptyHero said:**
> I don't know how to do what you are talking about, however if you want to watch a video full screen on your TV and still be able to browse the internet and what not, its not very hard. 

Under X Server Display Configuration (in Nvidia X Server Settings of course) click on your TV. If you do not see it, make sure the cables are connected and hit detect displays.

Then hit Configure... and click on TwinView and then Ok. 

Under Position, select the position of your TV. If it is the right of your monitor choose right, although anywhere will work. 

Then I suggest choose the highest resolution your tv/cable connector can do. Hit apply, and you should be good to go.

For some reason though, whenever I do this I end up getting the panels and such on the tv screen instead of the monitor. I get around this with the following:

Click on your monitor icon, and make sure 'Make this the primary display for X Screen' is checked.

Click back on the TV icon, and then make the position of the screen above. Apply, and tell the dialog you want to keep these settings.

Change the position back to the original one you had it on (it is right for me) and apply and keep the settings. (So for me, I originally had it right of screen, then put it above of screen, and then back to right of screen)

This fixed that issue with me.

Now, to view a movie on the TV, open the movie and drag to the edge of the screen where you put the TV (right for me). You will be able to drag it onto your tv. Make it full screen as you normally would, and then bring your mouse back to your monitor.
are you using the s-video cable connection on the nvidia graphics card  when you do that?

---

### Post by HalfEmptyHero on 2010-03-20
Yes I am.

---

### Post by RED666 on 2010-03-21
B.t.w the nvtv application seems to me to be made redundant / obsolete
by the NVidia package for the GeForce6200. When I use it, it doens't seem to do anything but f* up my display settings. Also it doesn seem to have any gui that tells you what it&#347; doing.

**I have come to the conclusion that what I want (having a movie playing in a window on main screen and simultaniously fullscreen on my TV) might just not be possible (easilly).**

I did find some software that I didn't try yet ( [http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page) ) whitch might solve (part) of my problem. On WindowsXP I found that my software from my TV capture card was great for playing movies on my TV (much like solution below).
 and
 a youtube( [http://www.youtube.com/watch?v=GdTNvBBGk58](http://www.youtube.com/watch?v=GdTNvBBGk58))  movie that shows exactly what I'&#7743; trieing to achieve. 

Other questions:
Is it  possible to link a display / screen  a specific workspace?

Am I correct in assuming that you need to start the NVidia X Server configutation tool from the terminal with "sudo nvidia-settings" ?
If I don't do this it doesn't seem to be able to save changes in xorg.con and the changes don't get applied.

---

### Post by molar on 2010-05-13
although you are talking about nvidia, I having the same problem with ATI 9550 card. this is called Full Theater mode in the Windows driver, but I didn't succeed to make it work in ubuntu 9.10.

I'm sure this is simple as it sounds, since it's a feature that works flawlessly in windows. The driver actually sends the Overlay video to the TV in full screen. Everything on the first screen works as usual (you can see the desktop and the video in the player windows) but the video on the TV is always played in full screen. 

in windows it also happens when the screens are in extend mode and note clone mode.

---

