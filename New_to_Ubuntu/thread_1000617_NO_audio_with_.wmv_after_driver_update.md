---
title: "NO audio with .wmv after driver update"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by interceptorV8 on 2008-12-03
Okay...
video card: nVIDIA 256 MB GeForce 7300 GS,

I downloaded and used that program EnvyNG to help get the proper drivers for the video card.  It worked.  Everything looks better... meh, better than it did at least give or take a few hiccups.  BUT now for some reason... it must have messed up something because when I try to play my wmv. files, there's no audio.  i've looked a bit through other forums and everywhere i see, people keep saying to download the w32 codecs, but i already have them.  any ideas? suggestions?

---

### Post by Michael.Godawski on 2008-12-03
Try to remove the w32 codecs and install them again.

Also have a look at this older thread, perhaps it will work for you too:
[http://ubuntuforums.org/showthread.php?p=136306](http://ubuntuforums.org/showthread.php?p=136306)

---

### Post by interceptorV8 on 2008-12-03
do you know the "sudo" line to remove it?



**okay...i think i got it working now....   thank you :)

---

### Post by interceptorV8 on 2008-12-03
okay, well in larger .wmv files, the audio falls out of sync...  i checked my "~$ gedit ~/.xine/catalog.cache" file and see there's two sections with w32 in them and i noticed that it's "1.20" instead of the 1.0.0 i've read about.  i changed both decoder priorities to 7

1:

[/usr/lib/xine/plugins/1.20/xineplug_decode_w32dll.so]
size=158992
mtime=1217964374
type=131
api=15
id=win32a
version=10111
supported_types=50593792 52428800 52822016 50724864 50790400 50855936 50987008 51052544 51118080 51183616 51380224 53346304 54001664 
decoder_priority=7

2:

[/usr/lib/xine/plugins/1.20/xineplug_decode_w32dll.so]
size=158992
mtime=1217964374
type=132
api=18
id=win32v
version=10111
supported_types=36044800 33816576 33882112 34013184 34078720 34144256 34209792 33685504 34340864 34406400 34930688 34996224 34799616 34865152 37158912 35127296 36110336 36372480 37093376 37814272 37879808 37945344 
decoder_priority=7

---

