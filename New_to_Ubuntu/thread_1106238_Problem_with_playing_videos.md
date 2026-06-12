---
title: "Problem with playing videos"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Sandertje on 2009-03-25
Hello,

I'm new to ubuntu, or any linux distribution. I just installed it a few days ago on a somewhat older computer (4~5 years). 

I'm having some troubles with playing videos. I've already followed this thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) but without succes.
Totem, or VLC - I've tried that as well - stop working a few minutes into the movies. It just stops. Sometimes, the video will go into fast-forward modus after a while. When that happens, the sound won't go into fast-forward, so that video and sound go asynchronous. 

The files are on an external HD, which has an NTFS filesystem. Could that be the problem? Because with a few times I tried to watch a video, the icon for the HD in nautilus just vanished when the video stopped.

---

### Post by germanix on 2009-03-25
Hi, I am assuming that you run Ubuntu 8.10 The first thing I would suggest you do is running this command in a terminal;
Go to applications, accessories, terminal
Then copy the following command and paste it in the terminal and hit the enter button

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

When it's all done you should be set set.
Hope this sorts out your problem

---

### Post by Sandertje on 2009-03-25
Yes, you were right to assume I was using 8.10. Stupid of me not to mention that :p

I already installed most of those. The only thing new was the libdvdcss2. The problem's still there, only it seems that part of it is working. The video still stops, but after a minute or so the video continues, but it skipped the time it was dormant (I mean to say, that if it stopped at 2:00 minutes, and continued 1,5 minutes later, it started playing at 3:30 minutes. It just skipped those 1,5 minutes)

---

### Post by halitech on 2009-03-25
how much ram do you have? which video card? what processor? do you have compiz enabled? did you install the drivers for your video card?

---

### Post by Sandertje on 2009-03-26
I've got a Intel Pentium 4 2.80 Ghz processor
512 mb ram
ATI Radeon 9100 IGP/IXP200 

Compiz is enabled, and I did not install any additional drivers (when I go to system => administration => Hardware drivers, the list is empty)

---

### Post by networm1230 on 2009-03-26
hello every one to fix play back of some file formats you most get all the codec from the repository or add/remove. How to get codecs go to (applications) than go down to (add/remove) slect all and were it says show chose all available applications and search for (gstreamer) install all gstreamer available. these will help with different format videos/sound files playback.

or you can download VLC play. VLC play is a universal media player for video/sound files you can download it here [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/) or get it from the repository or add/remove.

---

### Post by halitech on 2009-03-26
try disabling compiz and seeing if you can get the proper driver for your video card, both should help

---

### Post by networm1230 on 2009-03-27
(compiz)  how to get playback of videos when using compiz open the compiz setting manager than go down to utility and click on video playback now you will have video playback in compiz fugin

---

### Post by Sandertje on 2009-03-29
Thank you for the tips, but the video playback was already enabled in compiz. 

Now, I've tried something myself. I tried to copy the video files to my home folder. That was unsuccesfull. After a few MBs, the transfer just stops. So, I may not be looking at a video playback problem, but at a problem with my external HD. Could that be it?

EDIT: when I finally got to copy an entire file, it just played that copied file perfectly. So I'm pretty confident it's not a playback problem, but a problem with my external HD. I've got a LaCie USB Mobile Disk (250 GB). Here's a link to their product page: [http://www.lacie.com/uk/products/product.htm?pid=10990](http://www.lacie.com/uk/products/product.htm?pid=10990) Dunno if that's enough information.

---

