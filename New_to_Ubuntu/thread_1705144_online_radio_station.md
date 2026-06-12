---
title: "online radio station"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by aussielinuxguy on 2011-03-11
Hi, Can someone help me out with a radio station called casey 97.7 FM in Australia. i am trying to listen to.  The web site is [http://www.3ser.org.au/](http://www.3ser.org.au/).

Up the top right of the screen it says LISTEN LIVE,when i click on the link it asks to open using mplayer, but nothing happens.

Is there a program i can use to listen to it ?

aussielinuxguy.

---

### Post by Frogs Hair on 2011-03-11
The station requires Moonlight , which is a Linux version  of  MS Silverlight . I just tested the station and it works with my Moonlight plug-in.
I have Gstreamer plug-ins as well.

---

### Post by davidmohammed on 2011-03-11
hmmm - I've just a standard maverick install but with ubuntu-restricted-extras installed as well.  The link works fine and plays automatically with totem

---

### Post by COMPUTIAC on 2011-03-11
Hello , I clicked on the link, clicked on Listen Live . It comes in loud and clear. 

  I have no extra add-ons, maybe flash-player ?

---

### Post by aussielinuxguy on 2011-03-11
Thanks for your replies. I installed moonlight-plugin-mozilla but when i go to the site and click on LISTEN LIVE a box appears on the screen asking to open with mplayer.

I click on it open and it downloads a file then nothing happens.

---

### Post by ikt on 2011-03-11
> **aussielinuxguy said:**
> Thanks for your replies. I installed moonlight-plugin-mozilla but when i go to the site and click on LISTEN LIVE a box appears on the screen asking to open with mplayer.

I click on it open and it downloads a file then nothing happens.

If you right click on listen live, and save the file to your desktop, then right click on that, and open with totem/movie player, does it play?

---

### Post by aussielinuxguy on 2011-03-11
ikt i did what you said, and it does nothing.

---

### Post by uRock on 2011-03-11
You may need to install ubuntu-restricted-extras within the Ubuntu Software Center.

---

### Post by ikt on 2011-03-11
> **aussielinuxguy said:**
> ikt i did what you said, and it does nothing.

bugger :/

When you say does nothing, do you mean nothing happens at all or totem opens but nothing plays?

---

### Post by aussielinuxguy on 2011-03-11
I installed totem player and now it works. Thank You all for your quick replies and help.

---

### Post by andrew.46 on 2011-03-12
Runs quite nicely from the commandline MPLayer btw:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer mms://118.107.184.201/3SERLive[/COLOR]**
MPlayer SVN-r33030-4.5.2 (C) 2000-2011 MPlayer Team

Playing mms://118.107.184.201/3SERLive.
STREAM_ASF, URL: mms://118.107.184.201/3SERLive
Resolving 118.107.184.201 for AF_INET6...

Couldn't resolve name for AF_INET6: 118.107.184.201
Connecting to server 118.107.184.201[118.107.184.201]: 1755...

Connected
unknown object
unknown object
file object, packet length = 1650 (1650)
unknown object
stream object, stream ID: 5
unknown object
unknown object
data object
mmst packet_length = 1650
Cache size set to 64 KBytes
Cache fill: 19.22% (12596 bytes)   

ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Audio stream found, -aid 2
[asfheader] Audio stream found, -aid 3
[asfheader] Audio stream found, -aid 4
[asfheader] Audio stream found, -aid 5
Clip info:
 title: 3SER Live Feed
 author: 3SER 97.7FM
 copyright: South Eastern Radio Association Inc.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 8.0 kbit/6.25% (ratio: 1000->16000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:1677236.0 (465:53:56.0) of 1844674428928.0 (512409563:35:28.0)  0.1% 4%

```

---

### Post by aussielinuxguy on 2011-03-12
andrew, i just tried it with the command line and your right, it does play nicely.

---

