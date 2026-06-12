---
title: "Kissed Windows Goodbye. Euphoria fading, could use advice. (playing Video/movies/DVD)"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by ehtoft on 2009-03-24
After months of arguing with the wife, I finally waved goodbye to Windows XP - Cold Turkey. I'm only a program user and know little of the workings behind graphic interfaces. I installed 8.10 without any problems on a HP Laptop and even managed to get the wireless working (just activated the hardware with downloaded drivers.)Looking at most of these posts, I feel a little stupid putting this up, but I can't seem to get Totem or vlc or Banshee or Kaffeine to play "avi" files or DVD's or probably any video file type - obviously a big part of the modern PC experience. What should be my first line of attack? Thanks for the patience so far.

---

### Post by freak42 on 2009-03-24
welcome to ubuntu.

there is an exhaustive faq, which probably will answer many of your (upcoming) questions.

it also helps you setup your dvd and video codec stuff:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#DVD_Playback_Capability)

hth

---

### Post by Lunx on 2009-03-24
Just wondering if you have installed the gstreamer plugins via Synaptic. There are some codecs in what they call the "bad" and "ugly" sets that you need to play some types of media files (audio and video). VLC, Totem and Mplayer all work fine on this machine, VLC in particular, very smooth playback and decent image quality.

And on a different topic, you may find the [_Pocket Guide_]("http://www.ubuntupocketguide.com/") very helpful for a good basic grounding in how Ubuntu works.

---

### Post by Anthon on 2009-03-24
If the automatic initiation of downloading of codecs doesn't work, or if you cannot figure out what to do there, I recommend installing vlc
  sudo apt-get install vlc

---

### Post by ehtoft on 2009-03-24
Me thanks you both for very quick responses! Sneaked a peek away from duties here at work - I will check this out when I get home later this evening (Norwegian time) and hope all goes well so wife can't say, "I told ya so!".. I'll post my results in about 8 hours or so... thanks again!

---

### Post by Onesimus on 2009-03-24
I follow the instructions in this posting to get everything working.

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Hope this helps.

---

### Post by lovinglinux on 2009-03-24
> **Onesimus said:**
> I follow the instructions in this posting to get everything working.

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Hope this helps.

+1

This tutorial is great. I never had a problem with video playback after following it.

---

### Post by Lunx on 2009-03-24
I notice in the OP that you mention trying Kaffeine. I see there's a player engine you probably need in order to get the gstreamer plugins to work with Kaffeine

> Gstreamer engine for kaffeine media player
Kaffeine is a media player for KDE. While it supports multiple player
engines, its default engine is Gstreamer, giving Kaffeine a wide variety of
supported media types and letting Kaffeine access CDs, DVDs, and
network streams easily.

This package provides the Gstreamer playing engine for Kaffeine.

Homepage: [http://kaffeine.sourceforge.net](http://kaffeine.sourceforge.net)

Install it either through Synaptic, or open a terminal and enter 

```
sudo apt-get install kaffeine-gstreamer
```

As an aside, when I came to Ubuntu I also got rid of XP so I was "forced" to learn the new way of doing stuff without the temptation to run back to Windows when things got a bit tricky (which has hardly happened, a problem getting Google Earth to run is about the only trouble I've had in the three months I've been using this OS, and perseverence saw me get that sorted eventually).

---

### Post by billgoldberg on 2009-03-24
The first thing I do after installing Ubuntu is running this command in a terminal;

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

When it's all done you are set.

---

### Post by raymondh on 2009-03-24
> **lovinglinux said:**
> +1

This tutorial is great. I never had a problem with video playback after following it.

Another tutorial I found useful was this

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

It may have been slight overkill (in my case, I just use VLC) but it seems to cover all I need for day-to-day computing

Hope this helps.

---

### Post by ehtoft on 2009-03-24
Just got home to try some of these great suggestions. Really really cool to get help this way, and some day I'll hope to give something back. However, though I seem to have installed plugins, I still don't have successful video (DVD) viewing. I installed a couple different players after failing in Mplayer (vlc and kaffeine). What I get irrespective of player is a split-second attempt at start up before the player vanishes like magic - turns itself off. Weird. So it's a problem where? Something common to all players... greatful for more suggestions.

---

### Post by philinux on 2009-03-24
Try some of these sample video formats.

Totem should play most automatically. Just click a link to play it. Or right click as it says.
[http://www.jhepple.com/support/sample_movies1.htm](http://www.jhepple.com/support/sample_movies1.htm)

---

### Post by carml on 2009-03-24
> **ehtoft said:**
> Just got home to try some of these great suggestions. Really really cool to get help this way, and some day I'll hope to give something back. However, though I seem to have installed plugins, I still don't have successful video (DVD) viewing. I installed a couple different players after failing in Mplayer (vlc and kaffeine). What I get irrespective of player is a split-second attempt at start up before the player vanishes like magic - turns itself off. Weird. So it's a problem where? Something common to all players... greatful for more suggestions.
Look under System->Help & Support->Music,Video & Photographs,you'll find there the complete instructions to play DVDs.:) 

Welcome on Ubuntu:):):)

---

### Post by ehtoft on 2009-03-24
No go there either. Same kind of problem. The movie never starts and it just strikes. I tried 6-7 down the list. Thanks nonetheless. I'm thinking it's something simple, yet obviously ridiculously elusive. (Despairing, but I'll keep it to myself until she (wife) wants to view something from this Laptop.) I ain't going back no matter what. More than anything - aside from all the frustration with the program side of things in Windows, the corporate Empire Speak wont emancipate us from ourselves. Our commonality is our only hope in these times.... Keep em coming. i'll try whatever it takes..

---

### Post by carml on 2009-03-24
So tell us what did you install,if something is still needed we can notice and say it to you.

---

### Post by mangurt on 2009-03-24
Just a quick question, but did you install libdvdcss?  I did not see that mentioned anywhere.

---

### Post by ulfj on 2009-03-24
I had the same problem then tried the obvious and clicked on the "ubuntu help" tab on the start page and followed the directions and did what it said and viola DVD's play.Don't tell your wife it was that ez though let her think your a genious.

welcome to ubuntu

---

### Post by LowSky on 2009-03-24
open add/remove and look for ubuntu-restricted-extras
or open a terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

as for DVD playback open terminal and copy and paste all this nice stuff
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

reboot gnome and everything should work

---

### Post by stchman on 2009-03-24
> **ehtoft said:**
> After months of arguing with the wife, I finally waved goodbye to Windows XP - Cold Turkey. I'm only a program user and know little of the workings behind graphic interfaces. I installed 8.10 without any problems on a HP Laptop and even managed to get the wireless working (just activated the hardware with downloaded drivers.)Looking at most of these posts, I feel a little stupid putting this up, but I can't seem to get Totem or vlc or Banshee or Kaffeine to play "avi" files or DVD's or probably any video file type - obviously a big part of the modern PC experience. What should be my first line of attack? Thanks for the patience so far.

You need to install the proper CODECs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

You will be playing all the files now.

---

### Post by HousieMousie2 on 2009-03-24
Seriously, you should try what billgoldberg suggested if you have not already.  The medibuntu codecs and particularly libdvdcss2 should do the trick.

A bit of strangeness though... having multiple media players is a good idea.  MOST of my DVDs will play on VLC, but for some strange reason Disney tends to only work with Kaffeine for me.  Honestly between VLC and Kaffeine I have not found any DVD I can not play, but I say the more the merrier... after all, they are taking up WAY less space than Windows programs would.

> **billgoldberg said:**
> The first thing I do after installing Ubuntu is running this command in a terminal;

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

When it's all done you are set.

---

### Post by ehtoft on 2009-03-24
Been trying different stuff. Since everything was crashing/disappearing, I just went through the "system" menus, both preferences and administration, and came across "hardware drivers." Therein I found a ATI graphics driver that wasn't enabled. Did that, restarted and got the DVD to start in Totem Mplayer, but then it crashed "error couldn't connect stream". That happened right after I clicked the language menu to move on. Then I installed again vlc and kaffeine, both worked but with some annoying static (at least for a few minutes before I came back to this) So the Ubuntu Mplayer stalls. On the right track. Sorry to all you that suggested stuff that had no chance of working as long as the driver wasn't enabled... embarrassing... any idea on the problems with the Player installed with 8.10?

---

### Post by acreech on 2009-03-24
> **Onesimus said:**
> I follow the instructions in this posting to get everything working.

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Hope this helps.

The instructions in this thread has also helped me. I can watch a DVD with VLC  or Xine. Are you familiar with the terminal? That is where all the commands in the guide have to be put.

---

### Post by ehtoft on 2009-03-24
Ok. I've now gone through Dragon, Kaffiene, gxine, vlc, banshee. Only vlc seems to do both the avi files, DVD's with pretty good picture. Time to let a sleeping dog lie? Amazed to get this far. Ubuntu I will push on my mates - Now time to ask the wife if she wants to catch a movie...Thanks for all the help. I'll take heed if more info is necessary for totem Mplayer ("failed to connect stream" error), but am now out of the dog house...

---

### Post by raymondh on 2009-03-26
@ housiemousie2

"....MOST of my DVDs will play on VLC, but for some strange reason Disney tends to only work with Kaffeine for me"

I just discovered that now .... this Disney issue being brought up by my 8-year old son whilst using my computer.   Wonder why?

Like you.... VLC and now, Kaffeine.  Thanks for this heads-up.

---

### Post by theiron on 2010-03-27
> **billgoldberg said:**
> The first thing I do after installing Ubuntu is running this command in a terminal;

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

When it's all done you are set.
This did the trick for me.  I was able to do something similar yesterday, it got Movies to playback in both MoviePlayer and VLC, but Tv-series would stall in both.  This little ditty took care of the last tidbit needed to make EVERYTHING (well, I've not attempted DIVX yet) work with BOTH!

I am so happy, that I'm gonna take your command to a few threads that might use it.  Gems like these lie hidden until we stumble over them.

---

### Post by theiron on 2010-08-15
I am now SO close to joining the ranks of them's pitching Windows out the window. but I'm waiting for Ubuntu 10.10 with Blu-Ray built in to arrive.  Of course, Windows 7 has nothing that will run Blu Ray, not without spending another $100 or so.  And, it seems, that the platform that I'm running Win 7 on is not made for such an implementation, yet it loved Karmic Koala and loves Lucid Lynx.  On that platform, it dual-boots into Lynx or Win 7, and the Lynx is the Desktop version - seeing as this Inspiron 1520 laptop has duo-core and 2GB RAM, it rivals most desktops that I've seen.

Here's the quandary, I made all of these updates to the Koala and they somehow were brought forward in the rolling upgrade to the Lynx.  Oh, I still had to go get the B43-FWCUTTER drivers, but movies were no problem right out of the first boot into the Lynx.  

But, another, not so well endowed laptop is unable to play ANY DVD of any kind, and it is running a fresh new full installation of the Lynx.  I made scripts on the 1520 to assist in the reload should it become necessary, listing all of the installed packages and using a bin/sh to install them.  I engaged this set of installations on the B120 that is having the problems, and I can't get any closer, even after the bad and the ugly and the rest have been installed and the box rebooted.  The command stream given earlier fails miserably, because the medigbuntu site is no longer online.  I keep getting 404 errors when I try to run it.

---

