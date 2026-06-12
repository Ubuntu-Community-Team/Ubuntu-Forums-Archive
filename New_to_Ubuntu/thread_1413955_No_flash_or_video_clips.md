---
title: "No flash or video clips"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Glen007 on 2010-02-23
Hello,
I've just encountered a problem where videos and flash will not play on web sites.
For example, if I go to YouTube the page will load but the video box stays black and will not play, but the remainder of the page is there.
And flash areas on web pages have this big grey triangle which when clicked on will only then play the flash.
I've restarted the PC and re-opened FireFox but no change.
Any way I can do a "system restore" or similar?

Thank you.

---

### Post by Brindled on 2010-02-23
so, you were able to play flash vids fine at a previous time?

if so, what kind of changes have you made since being able to see them?

---

### Post by Robster2 on 2010-02-23
To run videos you have to install the restricted extras.

While connected to the Internet

Applications > Accessories > Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

That should fix it.

---

### Post by lovinglinux on 2010-02-23
You need to remove conflicting plugins and install only the adobe flash version.

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by thecliff on 2010-02-23
> **lovinglinux said:**
> You need to remove conflicting plugins and install only the adobe flash version.

For 32bit see [this]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2").

For 64bit see [this]("http://ubuntuforums.org/showthread.php?t=1358591").

This has always worked for me as well.  Choose your processor and then remove all previously installed Flash plugins (open source & proprietary) and then just install the one you need/want.

---

### Post by Glen007 on 2010-02-23
I tried the above method and was able to watch a couple of YouTube clips but they were very jerky, the frame rate appeared to be about 1 per second, then it stopped working again. 
As a side note, I have never been able to watch YouTube clips in full screen without it being very jerky in Ubuntu (no problems when I was running Windows), but it has been fine in the smaller view.
Yesterday I was trying to load a web building program through Terminal which didn't work, so I ended up installing Kompozer.
Also I have now noticed that when I open up Evolution, it keeps asking me for all the passwords for my mail box's which it never used to. Problem is, when I enter the passwords it just keeps asking me for them without downloading the emails.
So it appears I may have done something wrong whilst trying to install that web building program, but I have no idea how to reverse the issue.

---

### Post by lovinglinux on 2010-02-23
> **Glen007 said:**
> I tried the above method and was able to watch a couple of YouTube clips but they were very jerky, the frame rate appeared to be about 1 per second, then it stopped working again. 
As a side note, I have never been able to watch YouTube clips in full screen without it being very jerky in Ubuntu (no problems when I was running Windows), but it has been fine in the smaller view.
Yesterday I was trying to load a web building program through Terminal which didn't work, so I ended up installing Kompozer.
Also I have now noticed that when I open up Evolution, it keeps asking me for all the passwords for my mail box's which it never used to. Problem is, when I enter the passwords it just keeps asking me for them without downloading the emails.
So it appears I may have done something wrong whilst trying to install that web building program, but I have no idea how to reverse the issue.

Have you enabled the hardware drivers for your graphics card?

---

### Post by Glen007 on 2010-02-23
I'm just running the integrated chip for graphics at present.
Everything was working fine (apart from the glitchy full screen YouTube issue) until yesterday.
I can watch full screen videos and movie clips in Movie Player no problem, it appears to be just internet related. 
Especially with the flash issue and email password problem popping up at the same time.
If you can imagine a website that has a flash image on it, well now on my browser (Firefox) that image is just a big grey box with a circle and a triangle in it. If I click on that triangle the flash will play.
So it's not automatically loading for some reason.

---

### Post by lovinglinux on 2010-02-23
> **Glen007 said:**
> I'm just running the integrated chip for graphics at present.
Everything was working fine (apart from the glitchy full screen YouTube issue) until yesterday.
I can watch full screen videos and movie clips in Movie Player no problem, it appears to be just internet related. 
Especially with the flash issue and email password problem popping up at the same time.
If you can imagine a website that has a flash image on it, well now on my browser (Firefox) that image is just a big grey box with a circle and a triangle in it. If I click on that triangle the flash will play.
So it's not automatically loading for some reason.

The grey button means you are using gnash instead of the Adobe plugin. Follow the instructions on my first post, to remove the conflicting plugin, and restart Firefox.

---

### Post by no2498 on 2010-02-23
if all that does not work try this
open a terminal type ( gstreamer-properties ) click enter
click video set the top part of the video to xwindow to (no xv)
something is changing ive not got a hold on it yet
but that should help you

---

### Post by no2498 on 2010-02-23
you may need to restart the computer to make it work

---

### Post by Glen007 on 2010-02-23
I re-tried lovinglinuxs' method and it worked this time.
Videos are still very, very glitchy on YouTube when in full screen.
But at least it's back to where it was before.
When I did it this time it actually wouldn't play anything. After changing the plug ins in Terminal there was a prompt on the YouTube page saying I didn't have a flash player, so I just installed the Adobe one listed and it's working.
Thanks for all the help.
It's good learning these little things.

---

### Post by bullet311 on 2010-02-23
I suggest running the Update Manager and see if you are missing any important Adobe Flash updates.

---

