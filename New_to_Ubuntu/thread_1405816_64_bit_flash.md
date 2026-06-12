---
title: "64 bit flash"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Falc7 on 2010-02-13
Recently i have been unable to play youtube videos because it wants me to update flash. But it always links me to a 32bit version of flash. The flash i am using at the moment was the one from the restricted extras package. Can someone help?

I tried following this guide but it didn't help, possibly because i am using chrome
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by audiomick on 2010-02-13
Have a look at this
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

edit: and maybe this too
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Falc7 on 2010-02-13
It says i have the newest version installed now, but chrome still won't play YT vids, saying i need to upgrade

---

### Post by rajeev1204 on 2010-02-13
Delete completely the existing flash plugin with the command:

```
sudo apt-get remove flashplugin-nonfree
```

Now go to [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz) and download the 64 bit plugin to desktop and untar it.

Create the directory plugins under .mozilla with :

```
mkdir .mozilla/plugins
``` and move the player to this location.(Its hidden directory in home folder)


Restart the browser.

---

### Post by ikt on 2010-02-13
> **Falc7 said:**
> It says i have the newest version installed now, but chrome still won't play YT vids, saying i need to upgrade

if you have chrome:

[http://www.google.com/chrome](http://www.google.com/chrome)

join the html5 beta:

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by Falc7 on 2010-02-13
> **rajeev1204 said:**
> Delete completely the existing flash plugin with the command:

```
sudo apt-get remove flashplugin-nonfree
```

Now go to [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz) and download the 64 bit plugin to desktop and untar it.

Create the directory plugins under .mozilla with :

```
mkdir .mozilla/plugins
``` and move the player to this location.(Its hidden directory in home folder)


Restart the browser.

Will this work for chrome? i ask because you are talking about .moazilla

> **ikt said:**
> if you have chrome:

[http://www.google.com/chrome](http://www.google.com/chrome)

join the html5 beta:

[http://www.youtube.com/html5](http://www.youtube.com/html5)

I have now joined the HTML5 beta, and where the videos are meant to be is just black

---

### Post by rajeev1204 on 2010-02-13
> **Falc7 said:**
> Will this work for chrome? i ask because you are talking about .moazilla



I have now joined the HTML5 beta, and where the videos are meant to be is just black

Yes, chrome reads it from there.Iam using it.

---

### Post by Falc7 on 2010-02-13
> **rajeev1204 said:**
> Yes, chrome reads it from there.Iam using it.

Hm, daily motion plays fine, as does youtube when the video is embedded in a forum. But when i go to youtube where the video should be is just black

When i go here ttp://kb2.adobe.com/cps/155/tn_15507.html
It reports my flash version as the LNX 10,0,45,2

---

### Post by Falc7 on 2010-02-15
bump

---

### Post by tom.swartz07 on 2010-02-15
> **Falc7 said:**
> bump

Try using the link in my sig. It involves using the official Flash version 10.01 for x64 systems. Ive used that method and it has no problems whatsoever for me.

---

### Post by Falc7 on 2010-02-18
That script linked in your post, how do i run it? I tried saving it in kate then making it executable, but it didn't open

I've noticed youtube works fine in FF, its seems to be just chrome i have this problem with

---

### Post by Falc7 on 2010-02-20
I've noticed there is no folder:
flashplugin-installer in lib folder, should i make it?

I've noticed in synaptic, it lists my flash version as 10.0.45.2
This problem only happens in chrome, could it be something to do with the settings in chrome?

---

### Post by zaphod777 on 2010-02-20
First do a search on your whole HDD and delete every instance of libflashplayer.so

Then 
download the latest x64 version of flash from Adobe's web site 
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz) 

extract the tar and copy libflashplayer.so to /usr/lib/mozilla/plugins/.

After that first test in firefox then test in Chrome.

That should be it. 

If you have different versions everywhere it will cause a lot of problems.

---

### Post by Falc7 on 2010-02-20
Does that mean uninstalling kubuntu-restricted as well?

---

### Post by zaphod777 on 2010-02-20
> **Falc7 said:**
> Does that mean uninstalling kubuntu-restricted as well?

Not the whole thing just make sure that the 2 packages:
flashplugin-installer
flashplugin-nonfree

Are removed as well as libflashplayer.so that is in any folder on your HDD. 

Then just download and put it in the one folder I stated in my other post.

I had the same problem as you before.

I had a working flash then the restricted extras over wrote it so I had to make sure I removed the flash everywhere and then put the correct version in.

---

### Post by Falc7 on 2010-02-20
I did what you said, and deleted my cookies as advised here:
[http://www.google.com/support/forum/p/youtube/thread?tid=66bf17cbe7553e68&hl=en](http://www.google.com/support/forum/p/youtube/thread?tid=66bf17cbe7553e68&hl=en)

All fixed :D thanks

---

### Post by zaphod777 on 2010-02-20
No problem drove me nuts for a while too.

---

