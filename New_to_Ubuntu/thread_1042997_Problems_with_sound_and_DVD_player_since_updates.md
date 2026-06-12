---
title: "Problems with sound and DVD player since updates"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by huntergatherer on 2009-01-18
Hi, my brother recently bought me a computer with Ubuntu 8.04 installed.  I noticed the update manager was saying there where over a thousand updates available, and my bro suggested I downloaded them.  Since then the sound, which was working fine, doesn't work at all.  I get an error message: [I]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. 
[/I]
Also when I tried to play a DVD, which again had previously worked, nothing happened.  Previously it had automatically loaded on LinDVD, now the DVD_VIDEO icon appears on the desktop, but if I try to play it with LinDVD nothing happens.  There's no error message.

Although I've been using old versions of Ubuntu & Kubuntu for years  I've always gone to my brother to sort things out when I have a problem, but now he lives on the other side of the world, so I'm trying to deal with my technophobia and have a go myself!  I've tried to provide as much info as poss but I don't really know what I'm talking about.  I'd really appreciate some (idiot-proof) help!  :)

---

### Post by stoogiebuncho on 2009-01-24
I don't really know, but I'll reply just to bump this back to front page.

What happens when you open a terminal and enter 
```
alsamixer
```

---

### Post by huntergatherer on 2009-01-25
Hehe, thanks!  This happens: 

alsamixer: function snd_ctl_open failed for default: No such file or directory

I've been doing a bit of searching the forums.  I tried the sound problems comprehensive guide, and got to step 3 and found my sound card Intel Corporation 8280IH (ICH8 family) wasn't on the driver list.  I haven't managed to get any further than this.  Surely if it worked previous to the updates then it must have a driver?

Also, with the DVD problem it seems it may be a copyright problem. I found another thread who's problems sounded familiar [http://ubuntuforums.org/showthread.php?t=1045471](http://ubuntuforums.org/showthread.php?t=1045471) so i tried to follow the instructions to install the software to read commercial DVDs, but when I got to the final part, where I had to agree to the terms i couldn't click 'ok'.  I had scrolled all the way to the bottom. Don't know if this meant it didn't work properly, but now when I try to play DVDs with kaffiene (which I downloaded to see if that worked - it didn't) i get a warning about copyright but nothing more. However, i then found this thread [http://ubuntuforums.org/showthread.php?t=953199](http://ubuntuforums.org/showthread.php?t=953199) which says i shouldn't have installed (k/x/edu)ubuntu-restricted-extras and should remove it. When I tried what they suggest I got *E: dpkg was interrupted, you must manually run 'dpkg - -configure -a' to correct the problem.* I don't know how to do that, and am not sure this is the solution.

So yeah, there's a bit more info, help at all?

---

### Post by stoogiebuncho on 2009-01-25
Well, the way to run dpkg - -configure -a manually is simply to open a terminal window and type 

```
dpkg --configure -a
```

One other thing to try for DVD playback would be to install Medibuntu, if you haven't done that already.

Instructions: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Sorry I can't help with the sound issue. :)

---

### Post by huntergatherer on 2009-01-26
Erm, having tried that I got this... 

```
dpkg: requested operation requires superuser privilege
```

:?

---

### Post by stoogiebuncho on 2009-01-26
To run a command with supervisor privileges, just put a 'sudo' in front of it.  As in:

```
sudo dpkg --configure -a
```

It will ask you for your password, but won't give you any visual feedback (asterisks) when you type it in.  Just type it blind and hit enter and you should be good to go.

---

### Post by huntergatherer on 2009-02-01
As I wasn't having any joy I tried upgrading to 8.10, and my sound now works fine.  :D   

Thanks so much for your help!

---

### Post by stoogiebuncho on 2009-02-01
Great, I'm glad that worked for you.  :)

---

