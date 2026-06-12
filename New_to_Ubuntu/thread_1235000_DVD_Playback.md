---
title: "DVD Playback?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by mlthmp on 2009-08-08
Ok, im sure this has been answered before, but for the life of me I couldn't find it via search =( Im sorry for having to post, lol.

Im trying to get everything setup for everyday usage (just switched to Linux only yesterday) Anyway, im trying to get my computer to play DVDs.

I put a DVD in, I tell it to Search for suitable plugin.. and then I get the following.

No packages with the requested plugins found
The requested plugins are:
DVD source

And then,

An error occurred
The playback of this movie requires a DVD 
source plugin which is not installed.

Any suggestions are greatly appreciated

---

### Post by Nepherte on 2009-08-08
You need to install libdvdcss, a package you can acquire from medibuntu: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by CLomax on 2009-08-08
libcssdvd2?

Add the Medibuntu repo as directed above.

---

### Post by lisati on 2009-08-08
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mlthmp on 2009-08-08
installed from th following link,
[http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)  (I hope this was the correct one)

Tried to play a DVD and got the same message. Maybe I didn't install the right one? Again, im sorry if this is an "idiot's mistake" im only in my second day as a user lol.

---

### Post by mlthmp on 2009-08-08
> **lisati said:**
> [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

This worked. Thank you VERY much. Had to restart and use VLC. I appreciate the help

---

### Post by SunnyRabbiera on 2009-08-08
I personally suggest installing totem-xine, it will work with DVD's unlike the totem-gstreamer preinstalled with ubuntu (Totem is listed as movie player in your menu)

---

### Post by mlthmp on 2009-08-08
> **SunnyRabbiera said:**
> I personally suggest installing totem-xine, it will work with DVD's unlike the totem-gstreamer preinstalled with ubuntu (Totem is listed as movie player in your menu)

Done, and indeed it does work!

Question though. Is there a way to set something as default (say, set totem-xine to open DVDs instead of totem-gstreamer when a DVD is inserted?)  Right now when I put a DVD in the tray totem-gstreamer opens (which wont play DVDs)

I am trying to mutter my way through all this, Linux is a totally different beast than Im use to lol.

---

### Post by justsomedude on 2009-08-08
[QUOTE=mlthmp]
Question though. Is there a way to set something as default (say, set totem-xine to open DVDs instead of totem-gstreamer when a DVD is inserted?)  Right now when I put a DVD in the tray totem-gstreamer opens (which wont play DVDs)

I am trying to mutter my way through all this, Linux is a totally different beast than Im use to lol.[/QUOTE]

It should be impossible to have totem-gstreamer and totem-xine installed at the same time. I don't use Ubuntu, so take this with a grain of salt.

You could just remove totem-gstreamer. Also, you can define what happens when you insert a DVD under 
System -> Preferences -> Preferred Applications.

---

### Post by terry_gardener on 2009-08-08
click places - computer - edit - preferences - media (tab) 
under dvd option click the drop down  and select the app you want. 
click close

---

### Post by mlthmp on 2009-08-08
> **terry_gardener said:**
> click places - computer - edit - preferences - media (tab) 
under dvd option click the drop down  and select the app you want. 
click close

Worked! thank you very much =)


> **justsomedude said:**
> It should be impossible to have totem-gstreamer and totem-xine installed at the same time. I don't use Ubuntu, so take this with a grain of salt.


Hmm. Actually, it does show both under Computer / Pref / Media. So I dont know either, lol. As I said my second full day with Ubuntu installed. Do I need to remove the other one (totem-gstreamer) or do you think its OK to leave it as-is since now totem-xine is opening when I insert DVDs?

For DVD I have the following options,
Open Media Player (Xine)
Open Media Player
Open Disc Copier
Open VLC Media Player

---

### Post by terry_gardener on 2009-08-08
if it works it should be ok to have both. 
if get any problems however down the line you can always remove the gstreamer version.

---

### Post by mlthmp on 2009-08-11
Hmm. I hate to bring this up again =(

Tonight I decided to watch some DVDs. Tossed in one of my Star Trek DVDs, it played just fine. After that I popped in Ghostbusters and watched it. Both played fine.

Then, I decided to pop in Watchmen.. and nothing on my system would play it. 

Any suggestions?

*EDIT*

Wow.. well, now suddenly it starts working. Sorry guys

---

