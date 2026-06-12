---
title: "Firefox plugin problem?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by winjeel on 2009-05-10
I've tried to view the portfolios at Photo.Net through the Slideshows, but each time I do this it either shows nothing or crashes. For instance, try to view [this portfolio's slideshow]("http://photo.net/photos/migueldearriba"). What plugin am I missing, or what problem is there and how do I fix it?

Also, at my own website, I can't view my own slideshow, see [this homepage]("http://winjeel.com"), Though, I thought I allowed flash player to work on my Firefox.

---

### Post by pastalavista on 2009-05-10
You probably need the flasplayer-plugin. I'd recommend the adobe-flashplugin rather than the open source ones, even though you need to agree to their EULA.
```
sudo apt-get install adobe-flashplugin
``` Firefox will usually give you a message at the top of the screen to install missing plugins but in Jaunty, I don't know. The above command should fix it. Then restart Firefox.

---

### Post by kansasnoob on 2009-05-10
It would help to know what version of Ubuntu you're using. 8.04, 8.10, or 9.04?

---

### Post by winjeel on 2009-05-10
Jaunty (9.04).

---

### Post by collinp on 2009-05-10
Try running:
```
sudo apt-get install flashplugin-nonfree
```
then restarting Firefox.

---

### Post by kansasnoob on 2009-05-10
> **winjeel said:**
> Jaunty (9.04).

Good! That's the easiest yet!

Go to Synaptic and click on Search (not quick search or rebuilding search) and type flash! You should see only adobe-flashplugin and ubuntu-restricted-extras installed. Anything else should be marked for "complete removal" (same as purge remove in apt), especially gnash and any swfdec* (* being a wildcard).

You'll have to restart Firefox after the changes!

---

### Post by winjeel on 2009-05-10
Thanks. I can get YouTube videos working, but still the flash on my website doesn't work, nor the main presentation at [PhotoShelter]("http://http://pa.photoshelter.com/"), and the Photo.Net slideshows crash my browser. Is this a problem with the web applications, or my browser?

---

### Post by gandaran on 2009-05-10
> **winjeel said:**
> Thanks. I can get YouTube videos working, but still the flash on my website doesn't work, nor the main presentation at [PhotoShelter]("http://http://pa.photoshelter.com/"), and the Photo.Net slideshows crash my browser. Is this a problem with the web applications, or my browser?
the flash on your website is working fine with adobe flash, I think you mite have some open source flash installed like gnash or swfdec, any of these two installed wont let firefox use adobe flash, right click the flash video window, if it is adobe flash firefox is using then it should say something like adobe flash player 10 if it doesn't then it's something else.
and you also need to install java and java script enabled in firefox for the other website, install the sun-java6-plugin, find it in synaptic and install.

---

### Post by presence1960 on 2009-05-10
Are you using 32 bit or 64 bit Ubuntu? If 64 bit use this : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

But first it is advisable to remove all other Flash you have already installed. The above method from the x86-64 users section of the forums has worked flawlessly for me in Hardy, Intrepid and now Jaunty. I can view slideshows on the sites you linked to.

Plus here is a tip for Firefox Java plugin for 64 bit : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

That java plugin is way snappier than others I have tried. Thanks to zika for sharing that one!

---

### Post by winjeel on 2009-05-15
I've finally got round to doing it, and it works absolutely fine. Thanks, for the help.  :p

---

