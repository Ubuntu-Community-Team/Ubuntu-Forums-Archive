---
title: "IS IT POSSIBLE TO PLAY .Avi IN UBUNTU HELP!!!!"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by JORV on 2010-07-20
Tired of Windows I downloaded and installed Ubuntu about a week ago... so far it has been great, I have been playing around with it non-stop.... obviously I am completely new to linux... Anyways I had not had a problem until now... 

I downloaded one of my fav. TV series using transmission... all the files are .avi 
I can't watch any of them... I tried everything... VLC does not work... when I tried playing any of the files using VLC it doesn't show any images... just sound and a blank screen... I have installed all the VLC updates, divx codecs etc etc... done everything I have gather from the internet and all the forums...

My question is... Is there really a way to watch .avi files on ubuntu or should I just give up and delete them from my computer... if so is there a way to download torrents and watch them on Ubuntu

Thanks a lot 

J....

---

### Post by Mitchell Hale on 2010-07-20
Step 1- go to Synaptic
Step 2- Go to "Settings> Repositories" and check "Universe, Multiverse, and Restricted" (I'm not honestly sure which one it's in)
Step 3- Go back to Synaptic and reload (button in top left corner)
Step 4- Search for "ubuntu-restricted-extras"
Step 5- Install in the normal way (If you're that new, click box and hit "Mark for installation". Then hit apply)

---

### Post by 3rdalbum on 2010-07-20
Ubuntu understands AVI, but AVI is just a container format - you might need to install a codec corresponding to whatever video track is inside the AVI file.

The easiest way to do this is to install the "ubuntu-restricted-extras" package in Ubuntu Software Center.

If you still don't have any joy, then you might need the "w32codecs" package from Medibuntu. Go to [www.medibuntu.org](www.medibuntu.org) and follow the instructions for adding the repository, and then install the "non-free-codecs" package from there.

---

### Post by dineshs on 2010-07-20
Have you tried smplayer?

---

### Post by amsterdamharu on 2010-07-20
Strange, you installed vlc through synaptec package manager and selected the non free (universe) sources? I am using linux mint now and had no problem whatsoever playing any format so far. As for avi I can even play partially downloaded ones.

How about the video card, did you install a driver for it? (under *System*->Administration->*Hardware Drivers*)

---

### Post by utnubuuser on 2010-07-20
Might want to include an install of ffmpeg too - covers a lot of formats/toolsh

---

### Post by lovinglinux on 2010-07-20
See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"). All you need is there.

---

