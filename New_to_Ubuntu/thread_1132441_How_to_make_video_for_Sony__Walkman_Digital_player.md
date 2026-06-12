---
title: "How to make video for Sony  Walkman Digital players"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by lakedragon on 2009-04-21
I am putting this info up due to the problems that I had when I received a Sony Walkman digital player for Christmas.  With the little info that Sony provided I was only able to play the sample file. :(    After searching the web and various forums was I able to get some idea what settings were necessary to make videos for it.

I am using Ubuntu 8.10.  I use AcidRip to rip into .avi format.  I have tried the .mpg format, but have not been able to get a usable file from it.
To convert the .avi into .mp4, I use Handbrake.  The easiest way to do that is to set up a preset for Sony.  

Preset settings-

file extension: .mp4

screen size: 320 x 240 (this is max!  should be as close to this as possible!)

video codec: MPEG-4 (XviD)

framerate: 25

bitrate: 500 kbps

audio codec: AAC

bitrate: 128

sample rate: 44.1

Mix: Stereo
 
In the new version of Handbrake, you will have to make sure the screen size is set.  You can do this by selecting View from the menu. Click on Show Preview.  Once window opens, under Scaling, uncheck the Keep Aspect box.  Make sure you change the screen size to the 320 x 240.  or else as close as you can get.( 320 x 192 or 320 x 224 ).

Once video has been encoded to .mp4, you will have a file about 500 Mb.
These have a nice quality and even not to bad when using full screen on my laptop.

Hope this works for you! it has worked very well for me!:D

---

### Post by 3rdalbum on 2009-04-21
Well I'm glad you're getting video use out of your player, but there's been a program available to specifically do this since February last year :-)  Have a look at Blacklight on Launchpad.

---

### Post by lakedragon on 2009-04-22
Thank you for that info!  I had to searched high and low for any info at all! I have downloaded it and will try it out.
Once again, thank you!

---

