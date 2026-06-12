---
title: "Multimedia woes"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-06
Hi everyone.

First of all, I wanted to say thank you to everyone who's helped me already. Thanks in part to this forum I'm resolving my issues one by one.

Right now I'm having some problems playing multimedia files. I'm hoping there will be one or two things that will fix most of it.

I can play things on youtube and everything works fine but I have problems when I play stuff that's stored on the ntfs partition.

When I play videos with .mov .wmv .mpg and .mpe extensions, they play and the sound is fine and the video quality is fine but the screen keeps flickering. Actually, the window that the video is playing in flickers not the entire desktop. Sometimes I can see the window underneath as it flickers.

Other files with .rax .wma and dvr-ms extensions don't play at all.

Mp3 files will play but they just don't sounds as good as when I play them in windows.

---

### Post by lovelyvik293 on 2008-12-06
Please always post your system configuration with these problems.

---

### Post by Chris Hansen on 2008-12-06
> **lovelyvik293 said:**
> Please always post your system configuration with these problems.

Do you mean like the hardware and stuff?

I have a fairly new Dell Inspiron 530 pc, it looks like the video card is ATI Radeon HD 2400 PRO. It's a dual boot with Vista and a pretty basic installation of Ubuntu 8.1. The video driver is "ATI/AMD propriety FGLRX graphics driver.

I guess I'm not always sure what information is helpful, is there anything else I should list?

Thanks.

---

### Post by nhasian on 2008-12-06
try playing your media with VLC instead.  

```
sudo apt-get install vlc
```

see if that clears up your playback issues.

---

### Post by Chris Hansen on 2008-12-06
> **nhasian said:**
> try playing your media with VLC instead.  

```
sudo apt-get install vlc
```

see if that clears up your playback issues.

Thanks for the advice.

I tried it and, unfortunately, it didn't perform any better.

---

### Post by binbash on 2008-12-06
set the video output to X11 @ your video player's preferences

---

### Post by Chris Hansen on 2008-12-06
> **binbash said:**
> set the video output to X11 @ your video player's preferences

It worked! 

I changed the setting in VLC and the videos I tried seemed fine.

I looked for a similar setting in the Totem movie player and couldn't find one. Is there a setting there I can change?

Thanks a bunch!

---

### Post by Chris Watts on 2008-12-06
I have an ATI radon 2600 that is giving same problem - google earth is really bad, youtube is fine but DVD's played from the NTFS partition are flickering in the playback window. Is this the same thing? I didn't understand the fix about x11 settings posted previously.

---

### Post by 3rdalbum on 2008-12-06
> **Chris Watts said:**
> I have an ATI radon 2600 that is giving same problem - google earth is really bad, youtube is fine but DVD's played from the NTFS partition are flickering in the playback window. Is this the same thing? I didn't understand the fix about x11 settings posted previously.

Proprietary graphics card drivers are notoriously bad for not working properly with different output settings. In the preferences of your video player, there will be an option for changing the video output module. It's probably set to "default". Change this to any other type and see what happens.

For Gstreamer-based players like Totem, you need to go into "gconf-editor" and the gstreamer0.10 section to change the output module.

---

### Post by binbash on 2008-12-06
> **Chris Watts said:**
> I have an ATI radon 2600 that is giving same problem - google earth is really bad, youtube is fine but DVD's played from the NTFS partition are flickering in the playback window. Is this the same thing? I didn't understand the fix about x11 settings posted previously.

Nothing to do with google earth.Just disable compiz before opening it.install fusion-icon for easy switch if you dont want to mess with terminal.

I dont get any flickering issue on videos which are on ntfs drive.

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

read this and edit your xorg.conf

---

### Post by Chris Watts on 2008-12-07
I can't use accelerated graphics with windowed video... I have a laptop so I can't change the video card to something that will work with Ubuntu. Now I just have to wait for ATI to fix their driver and Google Earth will work too :-)

---

### Post by Chris Watts on 2008-12-08
> **binbash said:**
> Nothing to do with google earth.Just disable compiz before opening it.install fusion-icon for easy switch if you dont want to mess with terminal.

I dont get any flickering issue on videos which are on ntfs drive.

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

read this and edit your xorg.conf

I can leave compiz running if I use VLC instead of Totem etc. which is kinda good cos it rocks anyway.
I will just turn off compiz for Google Earth use.
btw the url above you suggested didn't work for me - the xorg.conf file wasn't configured in a way that the aticonfig tool was happy with and rather than spend hours going through man pages I opted to spend 10 minutes getting a new app that worked and a few seconds removing ones that didn't! lazy huh ;-)

---

### Post by Chris Hansen on 2008-12-10
> **3rdalbum said:**
> 
For Gstreamer-based players like Totem, you need to go into "gconf-editor" and the gstreamer0.10 section to change the output module.

Thanks for the suggestion. I'm kind of new to Linux and might need some more details though.

I did manage to find gconf-editor and found gstreamer0.10 but am not sure which setting to look for or how to change it.

---

### Post by unutbu on 2008-12-10
I've had good results following the advice on this page; perhaps it will help you too: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Chris Hansen on 2008-12-12
> **unutbu said:**
> I've had good results following the advice on this page; perhaps it will help you too: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I went through the whole thing and it didn't help, when I play video in most of the media applications the screen flickers. VLC seems to work fine since I set the video output to X11 but I can't find a setting like that in other applications like Totem. Isn't there a configuration file someplace where you can change that?

---

### Post by Chris Hansen on 2008-12-14
I got it!!

I found an old post with the answer:

[http://ubuntuforums.org/showthread.php?t=535920](http://ubuntuforums.org/showthread.php?t=535920)

For convenience I'll copy and paste the winning info here:

"If you are using the gstreamer backend then press alt+F2 and type

Code:

gstreamer-properties

Go to the video tab and change it to X Window System (No Xv)"

---

