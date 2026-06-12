---
title: "BBC videos"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by papyruswriter on 2008-12-21
I'm new to Ubuntu and know little about it. I'm not very computer savvy at all, so please be simple and explain manipulations. 

I'm an English teacher and often use BBC videos with my students. At the school I've never had a problem but they use windows. Now with my new home computer - Ubuntu Hardy Heron I can go to the BBC site but I can't see the videos. Also my computer often freezes when I access a site with media on it. Any ideas why? How can I rectify this problem.

On another site I was told to download plugins. Three were given as an alternative. I've now downloaded all but still can't access the videos. And my daughter can't access youtube either... not making for harmonious family life. Please help.

Papyrus

---

### Post by peter_brewer on 2008-12-21
You are missing the flash plugin.  You can install it either by looking for flashplugin-nonfree in Synaptic or alternatively running the following command in a terminal:
```
sudo apt-get install flashplugin-nonfree
```

Hope this helps.

---

### Post by ugm6hr on 2008-12-21
See the Multimedia link in my signature for a How-to get and install everything to do with media.

But, as mentioned, youtube works with flash.

---

### Post by ibizatunes on 2008-12-21
```
sudo apt-get install ubuntu-restricted
```
You will get a few extra like java which is usefull

Also mediubuntu 
[www.medibuntu.org/](www.medibuntu.org/)  will let you have even more restricted formats

[www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

is a good guide

---

### Post by papyruswriter on 2008-12-21
Thanks for your reply Peter but I've already got flashplugin-free and it still doesn't work.

---

### Post by ibizatunes on 2008-12-21
What version of ubuntu are you running? 8.04 or 8.10
What is your system x64 or x32 bit? x64 flash can be a problem, in 7.10 and below, 8.04 is better but still a bit buggy, 8.10 x64 flash works like a dream!!

Try installing ubuntu-restricted

---

### Post by Lutin on 2008-12-21
I'm using Ubuntu 8.04 and 8.10 (on different machines) and I'm sure that I had to install mplayer and mozilla-mplayer to get BBC content to work.

---

### Post by Tom--d on 2008-12-21
I've notice flashplugin-nonfree doesn't work.

Just go to Adobe flash side and download the .deb

Double click it.
Done.

---

### Post by mikewhatever on 2008-12-21
> **papyruswriter said:**
> 
I'm an English teacher and often use BBC videos with my students. At the school I've never had a problem but they use windows. Now with my new home computer - Ubuntu Hardy Heron I can go to the BBC site but I can't see the videos. Also my computer often freezes when I access a site with media on it. Any ideas why? How can I rectify this problem.

It's hard to advise without links to test. If BBC uses flash, then it's the same plugin you need for youtube, if not, give us some links.

> On another site I was told to download plugins. Three were given as an alternative. I've now downloaded all but still can't access the videos. And my daughter can't access youtube either... not making for harmonious family life. Please help.

Installing all three plugins was a bad idea, and you'll need to remove all but one. Can you post the outputs of the following commands from Applications/Accessories/Terminal:

dpkg -s flashplugin-nonfree
dpkg -s swfdec-mozilla
dpkg -s gnash

---

### Post by ibizatunes on 2008-12-21
I may know what the issue is!
Unistall Mozilla-vlc 
Also unistall mozilla-mplayer
vlc and / or mplayer is trying to play the flash content and it cant do it, the iplayer has changed to flash only now,  i think


```
sudo apt-get remove mozzila-vlc
```
```
sudo apt-get remove mozilla-mplayer
```

that will fix your issue

Close firefox and reopen it!

---

### Post by ajcham on 2008-12-21
> It's hard to advise without links to test. If BBC uses flash, then it's the same plugin you need for you tube, if not, give us some links.

I think most videos on the BBC site use Flash (and all the iPlayer ones do), however, a number of the videos still use Windows Media or RealPlayer formats.

---

### Post by mikewhatever on 2008-12-21
> **ajcham said:**
> I think most videos on the BBC site use Flash (and all the iPlayer ones do), however, a number of the videos still use Windows Media or RealPlayer formats.

I am not too familiar with the BBC site, but what videos I could find where flash and played ok. The iplayer videos is something I can't test because my geographic location is outside of UK.

> **ibizatunes said:**
> I may know what the issue is!
Unistall Mozilla-vlc 
Also unistall mozilla-mplayer
vlc and / or mplayer is trying to play the flash content and it cant do it, the iplayer has changed to flash only now,  i think

that will fix your issue

Close firefox and reopen it!

Is there any indication of any kind that those plugins are installed? They are not in the default Ubuntu installation, and the OP didn't mention installing them.:confused:

---

### Post by papyruswriter on 2008-12-21
Sorry folks but I just don't understand what some of you are getting at. Is there any way I've downloaded loads of plugins etc and nothing is working. It's confusing me totally. Is there any way I can begin again at the beginning; i.e. get rid of all these plugins and start again. Thanks for answering. I'll be back again tomorrow.

Papyrus

---

### Post by mikewhatever on 2008-12-21
> **papyruswriter said:**
> Sorry folks but I just don't understand what some of you are getting at. Is there any way I've downloaded loads of plugins etc and nothing is working. It's confusing me totally. Is there any way I can begin again at the beginning; i.e. get rid of all these plugins and start again. Thanks for answering. I'll be back again tomorrow.

Papyrus

That seems to be the case, and yes, you can start from the beginning, but first, we need to know what is installed in order to remove it.

---

### Post by ugm6hr on 2008-12-21
> **papyruswriter said:**
> Sorry folks but I just don't understand what some of you are getting at. Is there any way I've downloaded loads of plugins etc and nothing is working. It's confusing me totally. Is there any way I can begin again at the beginning; i.e. get rid of all these plugins and start again. Thanks for answering. I'll be back again tomorrow.

Papyrus

Try the multimedia link that I directed you to earlier.

As long as you pick the right tutorial (i.e. Intrepid vs Hardy / 32 vs 64-bit etc), it will remove any unnecessary plugins before installing ones that work.

---

### Post by papyruswriter on 2008-12-22
Warmest thanks to you all. Everything is working fine now.

Papyrus

---

