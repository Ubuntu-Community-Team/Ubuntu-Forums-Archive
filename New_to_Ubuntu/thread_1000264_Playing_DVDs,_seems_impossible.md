---
title: "Playing DVDs, seems impossible"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-02
Hi
I am finding it impossible to play DVDs on Ubuntu.
I have tried with lots of disks, and several media players.
Totem, goes unresponsive
Mplayer, takes ages, then says there are too many video packets in buffer
VLC seemingly does nothing
Can anyone help me?

---

### Post by LowSky on 2008-12-02
enter the command one after the other

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

reboot (CTRL+ALT+Backspace)

then use any player

---

### Post by Falc7 on 2008-12-04
Hi
The start up and menu screen now works perfectly, but once i click play movie, the picture and sound get SERIOUS distortions. I can see the movie is trying to play, but the screen is almost unrecogniseable

---

### Post by halitech on 2008-12-04
what are your system specs? ie. video card, ram, cpu? also, what version of Ubuntu?

---

### Post by mapes12 on 2008-12-04
This may help: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by billgoldberg on 2008-12-04
> **Falc7 said:**
> Hi
The start up and menu screen now works perfectly, but once i click play movie, the picture and sound get SERIOUS distortions. I can see the movie is trying to play, but the screen is almost unrecogniseable

Set the playback from you videos from OpenGl to X11 or Xvideo, it might help.

Also it could be compiz fusion (it could be, I never had that problem).

---

### Post by Falc7 on 2008-12-04
@ Mapes, thanks i'll take a look

It is an acer 4920
Intel graphics accelerator X3100
2GB Ram
Core 2 Duo T5250

@billgoldberg
How do i do that?

---

### Post by billgoldberg on 2008-12-04
> **Falc7 said:**
> @ Mapes, thanks i'll take a look

It is an acer 4920
Intel graphics accelerator X3100
2GB Ram
Core 2 Duo T5250

@billgoldberg
How do i do that?

In vlc:

Tools -> Preferences -> Video in the output dropdown menu.

Disabling compiz:

System -> preferences -> appearance in the last tab -> "none".

Then to switch it back on, tag "extra" instead of "none".

---

### Post by Falc7 on 2008-12-04
I've just tried both of those, but the distortions are still unchanged, i can post a screen shot if you like?

---

### Post by philinux on 2008-12-04
Intel graphics accelerator X3100

Sounds like the graphics driver is not working as expected.

System>admin>hardware drivers.

---

### Post by Falc7 on 2008-12-04
It says no proprietory drivers are in use on this system

---

### Post by philinux on 2008-12-04
Are any offered to be installed?

---

### Post by Falc7 on 2008-12-04
Nope

---

### Post by philinux on 2008-12-04
If I were you I start a new thread.

Title something like.
How do I install a driver for an Intel X3100 graphics accelerator.

I'm not familiar with this one.

---

### Post by LowSky on 2008-12-04
according to this the intel card isn't working well with Compiz at all

[http://ph.ubuntuforums.com/showthread.php?t=975026](http://ph.ubuntuforums.com/showthread.php?t=975026)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

---

### Post by Falc7 on 2008-12-04
i read in the thread i created that compiz can work
[http://ubuntuforums.org/showthread.php?p=6308434#post6308434](http://ubuntuforums.org/showthread.php?p=6308434#post6308434)


Its strange, the opening screen, licensing information, and 'carlton' sign all work fine at the start

Would anything on this link work?
[http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

---

### Post by Tom--d on 2008-12-04
Change the output to OpenGL or Xv (Xv with NO compiz tho)

Its a driver issue which you cannot solve.
The reason there is no driver listed in Hardware Drivers is because that application is for drivers which are closed source. Intel drivers are Open Source. They are enabled by default.
If you have effects on the desktop. You have 3D. Intel drivers are working properly.

---

### Post by Falc7 on 2008-12-04
Yep effects seem to be working okay.

I have changed the video output in VLC to OpenGL however the DVD still dosen't play. And i know the DVD is fine because it works in the same computer on Vista

---

### Post by crjackson on 2008-12-04
> **Falc7 said:**
> Yep effects seem to be working okay.

I have changed the video output in VLC to OpenGL however the DVD still dosen't play. And i know the DVD is fine because it works in the same computer on Vista

Try this [http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html](http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html)

It alwasy works for me.

---

### Post by Falc7 on 2008-12-05
> **crjackson said:**
> Try this [http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html](http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html)

It alwasy works for me.

I've just done that, unfortunately the screen still dosen't work

[[IMG]http://img168.imageshack.us/img168/7834/screendr0.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=screendr0.jpg)

It begs the question, if the drivers for intel are open source, why can't i play DVDs?

---

### Post by crjackson on 2008-12-05
> **Falc7 said:**
> I've just done that, unfortunately the screen still dosen't work

[[IMG]http://img168.imageshack.us/img168/7834/screendr0.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=screendr0.jpg)

It begs the question, if the drivers for intel are open source, why can't i play DVDs?

Wow, that is ugly... Mine has looked like that before too, I'll dig around some more and see what I can find.

---

### Post by crjackson on 2008-12-05
Okay, here is a test.

Do you have ANY DVD movies that are not copy protected (even home movie on DVD)? If yes, see if it has the same problem. It may be a long shot, but at least it will eliminate CSS handling.

If not, rip one of the DVD's to your HD (stripping encryptions in the process) and see if the content will play properly.

I have had a couple of instances where I couldn't play movies until I ripped them (in spite of the fact that CSS handling was installed).  Give it a shot and let me know what the dealio is.

---

### Post by stinger30au on 2008-12-05
its not the video card drivers, its the drivers for reading dvds. something is missing but i dont know what

i did have the same experice when i was playing round with mandriva 2009 one and using "movie player" i got the same result. i used vlc and it was fine

i wnet hunting thru add remove and from emeory i searched on add remove and i found a few extar drivers for dvd reading, from memeory it said somehting about block reading. i added i and restart it and it was all good.

sorry to be a bit vague, but i honestly believe  it is not the drivers for your video card causing this error.

those blocks you see on the video output is cos the dvd is not being decoded correctly

---

### Post by mc4man on 2008-12-05
While generally speaking it won't matter you should post what version of ubuntu your using.

Try going into your home folder (view -> show hidden files), find the .dvdcss folder and delete it.

Then try vlc again.

If still no go, open vlc from a terminal, then go file -> open disk and see what errors show.

For vlc 0.8.6 just use vlc in the terminal.

For vlc 0.9.x use vlc -vv  (start with -vv to limit the info, -vvv gives to much in this case.

---

### Post by Falc7 on 2008-12-06
@mc4man
thanks, i deleted that file, and it seems to be working now!
And thanks everyone else for your help :)

---

