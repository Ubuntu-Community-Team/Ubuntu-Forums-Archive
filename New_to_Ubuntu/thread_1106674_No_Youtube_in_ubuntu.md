---
title: "No Youtube in ubuntu?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Jackie999 on 2009-03-25
I've noticed playing youtube in ubuntu has always been hit or miss. Lately I find FF will just close a few seconds into a video now..but if I am lucky enough to get it to play, there is no sound.
Is there anything that will play youtube in ubuntu? 
Thanks...

---

### Post by llamabr on 2009-03-25
You're using firefox?  It should warn you that you need additional plugins.  Just follow the prompts for the flash plugin.

---

### Post by malditonuke on 2009-03-26
> **Jackie999 said:**
> I've noticed playing youtube in ubuntu has always been hit or miss. Lately I find FF will just close a few seconds into a video now..but if I am lucky enough to get it to play, there is no sound.
Is there anything that will play youtube in ubuntu? 
Thanks...


Not a web browser, but Totem Movie Player allows you to search for youtube videos and it plays them.  It actually plays them smoother on my machine in full screen than by using a browser.

To use it, run Movie Player and select YouTube from the drop-down list.  Then search for the vid you want using the search bar.

---

### Post by kiridude on 2009-03-26
in terminal: sudo apt-get install flashplugin-nonfree

the other open players are a bit buggy.

also check for ubuntu updates

---

### Post by kansasnoob on 2009-03-26
I would begin by running the following command in terminal:

```
sudo apt-get remove gnash swf-gnome swf-mozilla && sudo apt-get install ubuntu-restricted-extras
```

Then close Firefox by going to File > Quit, then restart Firefox and go to Tools > Add-ons > Plugins and be certain that only one instance of Shockwave Flash is installed. If more than one is installed disable one or the other. (*Note: for some reason unknown to me I've found that version 10.0.12 seems to work better sometimes than 10.0.22, but not always - if you go to Synaptic and search for flash you'll likely find one version listed as adobe-flashplugin and the other listed as flashplugin-nonfree*) So you may have to try one and then the other - trial and error.

Back in Tools > Add-ons > Extensions see what you have installed. I've found that having Flashblock installed helped greatly with flash related browser crashes. Just click on Get Add-ons and install Flashblock 1.5.8 or newer! There is an older version in the repos but it quit working well beginning with about Firefox 3.0.5.

I'm assuming this is not 64 bit!

---

### Post by kansasnoob on 2009-03-26
Oh, if that should get Flash working but you still have sound problems look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Be sure to follow only the steps specific to your OS (I think it says Intrepid in your sig).

---

### Post by Ammet on 2009-03-26
> **kansasnoob said:**
> Oh, if that should get Flash working but you still have sound problems look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Be sure to follow only the steps specific to your OS (I think it says Intrepid in your sig).

Was speaking with someone about this just last night - [http://ubuntuforums.org/showthread.php?p=6958984#post6958984](http://ubuntuforums.org/showthread.php?p=6958984#post6958984) 

I'm having this problem as well (Flash video is great, but no sound) and followed that post exactly and still have no sound with Flash videos. Sound everywhere else in the system works great, just not in streaming video. Know of anything further I haven't tried for when that guide doesn't help any? (I'd stick my woes there, but as you can see from the latest posts in the thread for the Pulse Audio guide, there's plenty of folks in the same state that still don't have any solution either.) Thanks if you know of something else.

---

### Post by sgosnell on 2009-03-26
I'm assuming you have increased the volume in the flash window.  By default it seems to be all the way down, and I often have to increase it.  It's the little speaker icon on the bottom right, usually.  If you've done that, I don't know, because I've never had any other flash audio problems.

---

### Post by Ammet on 2009-03-27
> **sgosnell said:**
> I'm assuming you have increased the volume in the flash window.  By default it seems to be all the way down, and I often have to increase it.  It's the little speaker icon on the bottom right, usually.  If you've done that, I don't know, because I've never had any other flash audio problems.


This is correct. Volume in the flash video itself is indeed all the way up.

---

### Post by Jackie999 on 2009-03-27
Well now I feel like a fool. The volume was zero'd out on the youtube URL. On the good side, it doesn't seem to be crashing after trying these fixes ..so thanks for the help !:lolflag:

---

### Post by Ammet on 2009-03-27
FIIIIIXXXXXED!! Man am I pumped! Have tried nearly every fix I could find on these forums and not a single thing worked! Finally came across this today - [https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/49779](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/49779)

The fix was given by user djclay2009 almost all the way to the bottom of the page. In short though, I had to disable my integrated sound card in my bios! That was all! My PC came with an upgraded sound card and for whatever reason, Ubuntu was still trying to deal with the integrated one when streaming video in Flash. I have no idea the why's behind it, but it is finally fixed!! WOO HOO!!

\\:D/

---

### Post by sgosnell on 2009-03-27
I find that about half the time, the volume starts at zero on a YouTube video.  After you set it, if you don't immediately click somewhere else to move the focus, the up/down keys control the volume, and if you scroll down with those keys, you kill the volume again.  It's not optimal, but it's what we get.

---

### Post by llamabr on 2009-03-27
Good one.  You should change the subject to reflect that the issue has been [SOLVED]

---

