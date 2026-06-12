---
title: "cannot download FLV."
date: 2010-12-10
forum: New to Ubuntu
---

### Post by mikee55 on 2010-12-10
I was trying to download my own movie, having lost the original!
Mike:sad:

[http://www.youtube.com/watch?v=tWooxIh71uE](http://www.youtube.com/watch?v=tWooxIh71uE)

---

### Post by ajgreeny on 2010-12-10
So, solved or not?  I'm not sure what you want.

If it's not yet downloaded get the firefox add-on "Download-helper" which will do just that for YouTube and many other flash and video sites.

---

### Post by Jay Car on 2010-12-10
> **mikee55 said:**
> I was trying to download my own movie, having lost the original!
Mike:sad:

[http://www.youtube.com/watch?v=tWooxIh71uE](http://www.youtube.com/watch?v=tWooxIh71uE)

Here's what I do when I want to save a You Tube video to my computer. I play the video and watch for the red bar to finish loading the video, then I open my "tmp" folder and drag the video to my desktop. That's it...I have to rename it, but that's no problem.

An easy way to find the tmp folder is Places> Computer> File system> tmp. I have the tmp folder shortcut on my Docky bar for times when I want to grab a you tube vid.

It actually took far longer to explain this than it does to save a video. I'm sure others can tell you even faster easier ways, but this method can work in the meantime.

---

### Post by ajgreeny on 2010-12-10
> **Jay Car said:**
> Here's what I do when I want to save a You Tube video to my computer. I play the video and watch for the red bar to finish loading the video, then I open my "tmp" folder and drag the video to my desktop. That's it...I have to rename it, but that's no problem.

An easy way to find the tmp folder is Places> Computer> File system> tmp. I have the tmp folder shortcut on my Docky bar for times when I want to grab a you tube vid.

It actually took far longer to explain this than it does to save a video. I'm sure others can tell you even faster easier ways, but this method can work in the meantime.
That is what I used to do as well, until I found Download-helper.  I used a simple script to copy the Flashx#x#x files from /tmp to my chosen folder in /home, and had a link to that script on my panel, so a simple click on the icon did the copying for me.
```
#!/bin/bash
cp /tmp/Flash* /home/user/Movies
```

---

### Post by philinux on 2010-12-10
Using 10.10 and the flash videos no longer appear in /tmp. I'd love to know where they're going now.

---

### Post by TeoBigusGeekus on 2010-12-10
> **philinux said:**
> Using 10.10 and the flash videos no longer appear in /tmp. I'd love to know where they're going now.

[http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/]("http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/")

---

### Post by philinux on 2010-12-10
[QUOTE=TeoBigusGeekus;10224000][URL=""]

First place I looked browser cache but quite a lot don't even appear in there.

---

### Post by Achilles124 on 2010-12-10
use the addon Downloadhelper of Firefox. Works for me.

---

### Post by TeoBigusGeekus on 2010-12-10
> **philinux said:**
> [QUOTE=TeoBigusGeekus;10224000][URL=""]

First place I looked browser cache but quite a lot don't even appear in there.

Now for something completely... weird.
I use Opera on Arch linux and I just bothered to look at my flash version.
It's 10.1.102.65-1. What's weird? All videos appear normally in my /tmp folder.
Could it be just an issue with firefox? Another reason to love Opera. :P

---

### Post by polardude1983 on 2011-02-11
I have found out how to download flv files that dont show up in the tmp anymore. I found this short guide it was confusing so hopefully my comments make it easier to follow. I believe this to be a 10.2 flash thing now

[http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92](http://n00bsys0p.wordpress.com/2011/02/10/how-to-download-flash-10-2-video-streams-in-linux/#comment-92)

---

### Post by Rytron on 2011-02-14
It was ideal when all videos showed up in /tmp regardless of the web browser being used. I now notice that no video from all browsers shows up in /tmp :confused:
Will the old way be brought back?

---

### Post by chetancrasta on 2011-02-24
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by Rytron on 2011-02-24
Thank you chetancrasta. But wouldn't flash need to be updated eventually?

---

### Post by chetancrasta on 2011-02-24
The latest version of Flash (10.2) is a feature update [http://www.adobe.com/products/flashplayer/features/](http://www.adobe.com/products/flashplayer/features/) not a security update.

If any security bugs are discovered in Flash 10.1, then one would  either have to upgrade or use Firefox with the older flash only to download videos (not for regular surfing).

Since the downgrade does not affect Chrome, one could use Chrome for regular surfing.

---

### Post by Rytron on 2011-02-24
I tried both Chrome and Google Chromium, neither videos from YT show in /tmp

Where would the cache folder for those 2 browsers be located?

---

### Post by chetancrasta on 2011-02-24
> I tried both Chrome and Google Chromium, neither videos from YT show in /tmp

As stated in both my previous posts, the procedure downgrades Flash only for Firefox. Chrome will continue to use the latest version of Flash.

---

### Post by TeoBigusGeekus on 2011-02-24
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by Rytron on 2011-02-26
> **TeoBigusGeekus said:**
> See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

Thanks.

---

### Post by JohnArbuckle on 2011-03-06
> **ajgreeny said:**
> So, solved or not?  I'm not sure what you want.

If it's not yet downloaded get the firefox add-on "Download-helper" which will do just that for YouTube and many other flash and video sites.
works great!

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by Rytron on 2011-04-10
> **chetancrasta said:**
> Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/2011...ash-files.html](http://davesource.com/Solutions/2011...ash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

Hi chetancrasta. That URL is incomplete!

---

### Post by chetancrasta on 2011-04-10
> **Rytron said:**
> Hi chetancrasta. That URL is incomplete!

Sorry. Here it is: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)

---

### Post by Rytron on 2011-04-10
> **chetancrasta said:**
> Sorry. Here it is: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)

Thank you chetancrasta. I appreciate it.

---

### Post by supergirlkara on 2011-04-10
My favorite way to download videos from YouTube and a variety of other sites is to use DownloadThemAll plugin for firefox. Not only does it support YouTube but it will also work for 100s of sites.

---

