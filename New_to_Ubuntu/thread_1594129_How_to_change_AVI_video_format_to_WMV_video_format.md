---
title: "How to change AVI video format to WMV video format"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by jonathanfrost on 2010-10-12
how can i change the video format of one video from AVi to WMV? I have a Sony Walkman MP3 video player model NWZ-E344. I am really trying to figure this out and hoping that I can..

---

### Post by vallvi on 2010-10-12
I'm using 'mobile media converter', which does the job ok. If it's not in your Ubuntu software center, you can google for it. They have an Ubuntu version.

---

### Post by jonathanfrost on 2010-10-12
> **vallvi said:**
> I'm using 'mobile media converter', which does the job ok. If it's not in your Ubuntu software center, you can google for it. They have an Ubuntu version.

any specific name it would be under?

---

### Post by Braik on 2010-10-12
Hi jonathanfrost,
 
Normally there is a soft on Ubuntu (at least on Lucid) called WinFF that is a audio video converter (on the multimedia applications) that does almost everything, and I have just checked and it can convert to WMV.
 
If you do not have it you just can install it form the repository, open it and just select the wmv profile and that it is.
 
Good luck

---

### Post by jonathanfrost on 2010-10-12
I appreciate the help. the program worked but every time I tried to put the video on my MP3 player it wouldn't read the video being on there.

---

### Post by Nightstrike2009 on 2010-10-12
Have you tried Winff from official repos?

It relies on gstreamer has a backend so its probably best to install "ubuntu restricted extras" first

Hope that helps :-)

To install go to terminal and type:

sudo apt-get install winff

enter your root password and let ubuntu work its magic.

Your problem maybe (But I don't know) that your player uses a "wrapper" to play its own files I had a sansa fuze that did that and you had to use "sansa media convertor" to add the wrapper so it could play it, I hope thats not the case has I don't know a way around that. :-(

PS: Perhaps use Oracle Virtualbox [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") to install windows virtually and use your windows software inside ubuntu on that maybe the answer.

---

### Post by anewguy on 2010-10-12
If you use VirtualBox, be sure to install the PUEL version as being directed to, and not the open source version in the repositories.  Without the PUEL version you can't access USB devices.

Dave ;)

---

### Post by andrew.46 on 2010-10-13
Hi jonathon,

> **jonathanfrost said:**
> how can i change the video format of one video from AVi to WMV? I have a Sony Walkman MP3 video player model NWZ-E344. I am really trying to figure this out and hoping that I can..

This type of device can sometimes benefit from a bit of trial and error, but you could always try windows media video and aac sound with FFmpeg as follows:

```

ffmpeg -i input_file.avi -s qvga \
       -vcodec wmv2 -b 512k \
       -acodec libfaac -ab 128k \
       output_file.wmv

```

and this would provide at least a *starting *point, based on a quick look at [the specs]("http://www.lasoo.com.au/offer/mp3-player-ipod-accessories/e-series-sony-walkman-nwz-e344-mp3-player-5-08cm-2-inch-lcd-screen-8gb-capacity-video-player-fm-tuner-long-life-battery-black/4jxguswkb.html") for such a device. Bear in mind that classically you would actually use *-acodec -wmav2* for the audio. You would need to adjust the bitrates as appropriate and fit out your copy of FFmpeg for [aac encoding]("http://ubuntuforums.org/showthread.php?t=786095").

Andrew

---

### Post by ft-Orchard on 2010-10-13
> **jonathanfrost said:**
> how can i change the video format of one video from AVi to WMV? I have a Sony Walkman MP3 video player model NWZ-E344. I am really trying to figure this out and hoping that I can..

Try "openshot". It can be installed via the software manager.
Nice video editor too. 

Or try "ffmpeg". that should not be to difficult.
```

ffmpeg -i myfile.avi -sameq ~/Desktop/myfile.[FONT=Verdana]wmv[/FONT]

```

---

### Post by L Campbell on 2011-03-17
> **Nightstrike2009 said:**
> Have you tried Winff from official repos?

It relies on gstreamer has a backend so its probably best to install "ubuntu restricted extras" first

Hope that helps :-)

To install go to terminal and type:

sudo apt-get install winff

enter your root password and let ubuntu work its magic.

Your problem maybe (But I don't know) that your player uses a "wrapper" to play its own files I had a sansa fuze that did that and you had to use "sansa media convertor" to add the wrapper so it could play it, I hope thats not the case has I don't know a way around that. :-(

PS: Perhaps use Oracle Virtualbox [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") to install windows virtually and use your windows software inside ubuntu on that maybe the answer.

I,too, am wanting to convert .AVI to .WMV so I followed your instructions here and it did convert my file.  However, I cannot figure out how to 'select' the file in the folder.

---

### Post by L Campbell on 2011-03-17
> **L Campbell said:**
> I,too, am wanting to convert .AVI to .WMV so I followed your instructions here and it did convert my file.  However, I cannot figure out how to 'select' the file in the folder.

OK, I've got it figured out now and the process seems to work well.

Thanks.

---

### Post by patrick_the_fat on 2011-03-19
Just a suggestion,

If you figure out what works, consider putting details of what you did to get it to work so that others don't have to go through the same thing.

Which software did you end up using?
What format?  Which codec?

I am using the same MP3 player, and I still have to do the same experimentation although the solution has been discovered already.

Just some food for thought.  Thank you.

---

