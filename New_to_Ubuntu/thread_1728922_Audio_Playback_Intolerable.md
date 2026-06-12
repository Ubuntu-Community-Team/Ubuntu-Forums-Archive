---
title: "Audio Playback Intolerable"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Bob Abouille on 2011-04-14
I run Ubuntu 10.10 on a Dell Inspiron with "Intel chipset" audio card (???).

Audio (and video) playback is characterized by:

1) crackling sound
2) jumps back and forth. I can observe the seek bar go from 00:07 to 00:05 to 00:09, etc., forever and ever.

What makes this even more frustrating is that files will play normally for about 5 minutes before f**ing up, but that only happens after a fresh boot. What is happening during the first five minutes, and how can I extend it?

I updated all gstream, I installed VLC to no avail, I installed fluendo upon installation...I want nothing more than to run Ubuntu as my main operating system, but I spend 90% of my computer time with audio or video playing.

I fear I might be falling through the cracks. Any help would be greatly appreciated.

---

### Post by Naggobot on 2011-04-14
This might be self evident (so please for give me) but have you tried

[https://wiki.edubuntu.org/DebuggingSoundProblems](https://wiki.edubuntu.org/DebuggingSoundProblems)

There are more links on the bottom of the page. 

There is also a very long thread about debugging pulse audio related problem. You might find some hints there.

[http://ubuntuforums.org/showthread.php?t=1477390](http://ubuntuforums.org/showthread.php?t=1477390)

Unfortunately other than this I can offer no more insight to your problem. I would suggest anyhow that you try to rummage through available material and try to provide more information (device type etc.) Maybe someone may have more info to give then.

---

### Post by deconstrained on 2011-04-14
Find out what sound chipset you're using.

sudo lshw -C sound

Search for it here:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
Find the corresponding kernel module name and find out if you're already using it:
lsmod | grep <module>

Chances are you're already using the correct module, but you never know. You might try going to the manufacturer's website and digging for drivers that they themselves created for Linux, if the one Ubuntu selected to use is giving you problems.

---

