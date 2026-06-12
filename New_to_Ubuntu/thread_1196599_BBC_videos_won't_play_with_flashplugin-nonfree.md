---
title: "BBC videos won't play with flashplugin-nonfree"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by zorblek on 2009-06-25
I can't get the flash videos on the BBC website to load properly in any browser. This happens with all videos; it's not just ones that are region-specific (I'm in the USA) or expired. As an example of a video that won't play, see [http://news.bbc.co.uk/2/hi/in_depth/8116024.stm]("http://news.bbc.co.uk/2/hi/in_depth/8116024.stm"). The player loads, but the actual video doesn't. I just get an endless loading animation.

This happens independently of which browser I'm using. I've tried it in Firefox, Opera, and Midori. I'm using the latest flashplugin-nonfree on Ubuntu Jaunty. What really baffles me is that another Jaunty install with flashplugin-nonfree plays the videos with no problem...

Any suggestions would be greatly appreciated. Thanks!

---

### Post by Divider on 2009-06-25
3 things, 1. did you get the one from the adobe website, they have a .deb for ubuntu 8.04+, it works perfect with jaunty.

2. is your video correctly configured? Drivers installed, xorg.conf updated? etc.

3. some websites, even though they run flash sometimes need an xvid or divx plugin.

---

### Post by masux594 on 2009-06-25
Hi.. try this command```
*sudo apt-get install flashplugin-installer flashplugin-nonfree *
```.. I've searched for my pc a lot for a flash plugin, and this work perfectly !!

Sysc, A

---

### Post by lovinglinux on 2009-06-25
It might be a conflicting plug-in. Check the Troubleshooting section of the tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)


> **lovinglinux said:**
> 

**Problems:**

[list][*] 
[*] **Can't play streaming videos**
[*] **Flash videos display only a symbol and won't start**[/list]

**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content. You can disable plug-ins through the Addons window. Open "Tools >> Addons", then select the "Plug-ins" icon, then select the plug-in you want to disable and click the "Disable" button. Unfortunately, this not work every time, so the best procedure is to remove the conflicting plug-ins.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.

---

### Post by zorblek on 2009-06-25
I forgot to mention in my original post that I have this problem only with the BBC videos. Flash videos work just fine everywhere else (as do most other videos).

This I got this version of Flash by installing ubuntu-restricted-extras. I actually used to use the version from the Adobe site a while back, but I had issues with it (I don't recall what now), so I changed it to this one. I tried reinstalling it, but it had no effect. There aren't any other Flash versions installed.

I don't think it's a codec issue, since the other Ubuntu machine doesn't have any codecs installed that this one doesn't, and it plays the videos with no problem.

---

### Post by ed021990 on 2009-06-25
do u have ubuntu 64 bit or 32 bit? this is actually quite important in the adobe world

---

### Post by zorblek on 2009-06-25
> **ed021990 said:**
> do u have ubuntu 64 bit or 32 bit? this is actually quite important in the adobe world

I have 32 bit.

---

### Post by njegbers on 2009-07-20
> **lovinglinux said:**
> It might be a conflicting plug-in. Check the Troubleshooting section of the tutorial [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")
I had the same problem. This is the answer. Thank you!

---

### Post by lovinglinux on 2009-07-21
> **njegbers said:**
> I had the same problem. This is the answer. Thank you!

You are welcome and thanks for the feedback.

---

### Post by rosswmcgee on 2010-01-12
FF works fine with BBC  and other viedo sites, but Opera will not play bbc videos though it plays the sound and all other videos? Any ideas?

---

### Post by rosswmcgee on 2010-01-12
I gave up on this topic in this forum/ installed mint/everything works.

---

### Post by 3dmatrix on 2012-03-10
I use Ubuntu 11.10 I can play video from other websites but those at BBC website do not work. Not only in Firefox but they do not work in Opera also. Adobe website shows i have the latest flash plugin installed.
Can any one please help.

---

### Post by llamabr on 2012-03-10
This thread is 2 years old.  Please do not rehash very old threads.  Instead, ask a new question if you have one.

---

### Post by lovinglinux on 2012-03-13
Closed. 

Please refer to new thread at [http://ubuntuforums.org/showthread.php?t=1939039](http://ubuntuforums.org/showthread.php?t=1939039)

---

