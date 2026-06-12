---
title: "VNC as a way to use PDA as secondary screen..."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by NEUR0M4NCER on 2008-06-04
This has got to be possible. In fact, I spoke to a chap on irc #ubuntuforums who showed me a screenshot of it working, but so long ago that he couldn't remember how he did it - and i've since lost the pic to a fresh install - one of the ones where you're so mad at the computer that you scream "***f*** you!!!***" at the screen and gParted the life out of it without thinking about all the little snippets of great info you're losing.


***GOAL:***

To have my filthy old iPAQ connected via serial (yeah, that's where I hit the problems) - and in it's lovely stand-up cradle, to my desktop, and show a stand-alone screen with media controls - maybe a custom Rhythmbox skin or similar - and have the touch screen working without stealing the mouse cursor (or even focus if possible) from the main desktop.

How hard can it be? :D

And if any uber-dudes out there needed any more urging, well...

[COLOR=blue]<whispers> windows can do it...[/COLOR]



Hope someone can help - I need to restore my partner's faith in Ubuntu after I spent two weeks getting Youtube to work with AMD64 Flash and deleting her Sims2 guys on the XP partition... :twisted: - she's loving Compiz Cube Sphere, but I think it'll take more than that to stop her proclaiming: "[COLOR="Magenta"]My laptop's better than your computer because it has Vista![/COLOR]" :roll:.

Regards

---

### Post by NEUR0M4NCER on 2008-06-05
... bump. Someone must have an idea.

---

### Post by wdaniels on 2008-06-05
> **NEUR0M4NCER said:**
> To have my filthy old iPAQ connected via serial (yeah, that's where I hit the problems)

Couldn't you install Linux on the iPAQ and use usbnet to connect the two? It would give you a lot more options to do something nice that way.

---

### Post by NEUR0M4NCER on 2008-06-06
Thanks for your reply.

I had a look at [usbnet](http://www.linux-usb.org/usbnet/), but to be honest, it looks... more complex than I was hoping for... Besides - the PDA doesn't have USB (it's OLD) - although if there is a 'simpler' way of using usbnet, then i'm sure I could fork out 10 or 12 quid for a slightly less old PDA with USB...

---

### Post by Quantumstate on 2008-06-06
I have plans for doing just about this with a media server that records TV (MythTV), and a hoped-for wireless remote control maybe running VNC.

I doubt any version of Winduhs Mobile can run VNC reliably (assuming there is a VNC for WM), so I suggest trying [Opie](http://opie.handhelds.org).  It's been a while since I tried it, but when I did it was superb.

---

### Post by jure1873 on 2008-06-06
I'm sure there is a vnc viewer for PDAs, cause I've installed it on a friend's PDA... I don't remember the brand, it was somethind like qtek. 
Is is possible to create a ppp connection over serial? If it is maybe it's possible to get it working. A second xorg should be started that accepts vnc connections from your pda so it doesn't interfere with you mouse cursor. 
I'm just thinking out loud...


[http://www.cs.utah.edu/~midgley/wince/vnc.html](http://www.cs.utah.edu/~midgley/wince/vnc.html)

---

### Post by NEUR0M4NCER on 2008-06-07
> **Quantumstate said:**
> I have plans for doing just about this with a media server that records TV (MythTV), and a hoped-for wireless remote control maybe running VNC.

I doubt any version of Winduhs Mobile can run VNC reliably (assuming there is a VNC for WM), so I suggest trying [Opie](http://opie.handhelds.org).  It's been a while since I tried it, but when I did it was superb.

Have a look at [Innobec SideWindow](http://www.innobec.com/index.php?page=sidewindow) - it's absolutely beautiful, runs on Windows Mobile & XP/2k etc. Imagine (in the WinWorld at least) a maximised Winamp on the second screen... Awesome - except you have to pay for it :(.

That's pretty much what I want, but for Linux (amd64), and if poss' seperate pointer confined to the seperate screen, so to use it as a control device more effectively, rather than a simple secondary screen.

On the Opie front, I gave it a whirl on my XDA Pro a few months ago. Very nice - SLOW - but nice. I reckon OpenMoko might be a better bet (when the FreeRunner's finally out and the OS is stable). At the moment, OpenMoko DOES run, but has a lot of bugs that are simply way beyond my level of expertise (i.e. none whatsoever).

---

### Post by NEUR0M4NCER on 2008-06-07
For those who don't click the link above...

[IMG]http://www.innobec.com/uploads/InnoColorful/sw_pocketpc.gif[/IMG]

This is what SideWindow looks like (from the Innobec Site). Nice, huh?

---

### Post by NEUR0M4NCER on 2008-06-15
bump

---

### Post by staghni on 2008-07-04
Hi, I am not the only who tries to use my old PDA as a second monitor!! :KS 
Sorry for my bad english.
Actually I tried to install Innobec Sidewindow with WINE but had no luck!
I use this software under windows it's  great! :cry:. 
In windows it creates a second virtual monitor that u can use as an extended desktop. If I go through  properties of this second monitor I find the Innobec drivers.
Then there is the innobec service server window where  you can change parameters of the visualization on PDA monitor (pixel visualization , deep of color... and it show the port used by this server)
Actually I am quite knew to linux so no ideas on how to use these info.
I hope these would be useful for someone else.
A screen capture : On the right side is the 2 monitor and the PDA monitor shows the top left part of it!
[[IMG]http://img405.imageshack.us/img405/6610/sidewindowvn3.th.jpg[/IMG]](http://img405.imageshack.us/my.php?image=sidewindowvn3.jpg)  
Waiting for good news.. :popcorn::)

---

### Post by unsungboxer on 2008-12-06
> **staghni said:**
> 
Actually I tried to install Innobec Sidewindow with WINE but had no luck! I use this software under windows it's  great! :cry:. 


I have also used this program in windows.  It absolutely rocks.  I was able to use my PDA as a secondary monitor where I can maximize winamp while running full screen web browsing on my full monitor.

Then I did some fun tests:
1.  I synced my PDA (htc touch) to my computer via bluetooth.  I started sidewindow, and it works as a wireless secondary monitor!
2.  I started my webcam, and drug it to sidewindow.  Now I can remotely stream video from my webcam to my PDA!
3.  I started up the winxp onscreen keyboard.  drug it to side window.  I can use my touchscreen to type on the OSK!


So what are some useful applications?
1.  Use it as a mini screen to run programs like winamp or windows media player.
2.  I plan to use it in my carpc setup.  It will be a bluetooth heads-up-display projector. simply by sticking it on my dashboard.

I have spoken to the creator of sidewindow asking for an Ubuntu port.  He said he is an ubuntu user, but right now their focus is a Vista port, which is a better business decision.

I hope someone takes the time to read this, to see how we could impliment this idea into Ubuntu.  It might also make sense for someone to create a device-application for Google's Android Linux... just a thought.

-Unsung

---

### Post by NEUR0M4NCER on 2008-12-08
Hi - nice to see the idea's still alive! TBH, I pretty much gave up on the idea. It's cool you managed to get in touch with SideWindow's dev, but as you say, it is obviously a better business decision to make a Vista port (given the fact that a Linux version would probably be free...).

I've been following the progress of Android porting onto other devices (in the hopes I will be able to get it on my TouchDiamond) at [XDA Devs](http://forum.xda-developers.com/showthread.php?t=402002), but it looks like Google's focusing more on Windows integration that native bloody Linux integration anyways!

---

### Post by unsungboxer on 2008-12-13
> **NEUR0M4NCER said:**
> Hi - nice to see the idea's still alive! TBH, I pretty much gave up on the idea. It's cool you managed to get in touch with SideWindow's dev, but as you say, it is obviously a better business decision to make a Vista port (given the fact that a Linux version would probably be free...).

I've been following the progress of Android porting onto other devices (in the hopes I will be able to get it on my TouchDiamond) at [XDA Devs](http://forum.xda-developers.com/showthread.php?t=402002), but it looks like Google's focusing more on Windows integration that native bloody Linux integration anyways!

The creator of sidewindow says he actually uses ubuntu at home and might make a linux version as a side project, but obviously its not a priority.

I agree its frustrating that the google android development has focused on windows integration first.  Seems kinda backwards.  We will need to wait for freelance developers to take on these projects.

---

