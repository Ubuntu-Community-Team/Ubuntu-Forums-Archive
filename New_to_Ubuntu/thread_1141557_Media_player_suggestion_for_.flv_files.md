---
title: "Media player suggestion for .flv files"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-28
What player can I use to play ".flv" files. My Totem media player needs a flash plug in but from my searches the plugin has problems (Ubuntu 8.04). I was thinking of trying another media player. Thanks for any suggestions.

---

### Post by s.fox on 2009-04-28
Hi,

I would recommend VLC media player.  [Here]("http://www.videolan.org/vlc/download-ubuntu.html") is a download link.

Hope this helps.

-Ash R

---

### Post by Maheriano on 2009-04-28
I would recommend VLC for all video files.

---

### Post by Tibuda on 2009-04-28
Totem can if you install the right codec. I'll post the package you need after some searching.

---

### Post by Spiritous on 2009-04-28
Vlc :)

---

### Post by Tibuda on 2009-04-28
I have not found what is the right package, but if you install those, you sure will be able to play flv in Totem:
[gstreamer0.10-plugins-ugly gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-really-bad]("apt:gstreamer0.10-plugins-ugly,gstreamer0.10-plugins-good,gstreamer0.10-plugins-bad,gstreamer0.10-plugins-really-bad")

---

### Post by jwaclawsky on 2009-04-28
BTW, I can't get MPlayer working either I get a series of error messages whenever I start it. The first message says "MPlayer interrupted my signal 11 in module:unknown" Anyone know how I might be able to fix it. It was in my synaptic package manager so I just installed it from there.

I also installed VLC and it works fine. Thanks! ...how do I make it my prefered video app when I double click any particular video file?

---

### Post by jwaclawsky on 2009-04-28
To danielrmt. I installed the packages you suggested and now Totem plays the flv files. Thanks!

---

### Post by Didius Falco on 2009-04-28
> **jwaclawsky said:**
> 
<snip> 
 
I also installed VLC and it works fine. Thanks! ...how do I make it my prefered video app when I double click any particular video file?

You can set them up by file types. Open Nautilus, navigate to a, for example, FLV file and right click it. Choose "Properties" and then the "Open With" tab. Thre will be a list of all the apps that are capable of playing that file type. Click the little radio button next to VLC and then VLC will open any FLV file you double click.

You can do the same for any other file types you want to default to a certain app all or most of the time. Then, if you ever do want to open a file with a different app, just right click it and use "Open With".

I hope this helps...

---

### Post by jwaclawsky on 2009-04-28
I don't see a "nautilus" on my system.   ...does it have another name. I have something called preferred applications but it doesn't do as much as you are suggesting???

---

### Post by Tibuda on 2009-04-28
> **jwaclawsky said:**
> I don't see a "nautilus" on my system.   ...does it have another name. I have something called preferred applications but it doesn't do as much as you are suggesting???

Nautilus is the default ubuntu file browser.

---

### Post by t0p on 2009-04-28
If anyone else is experiencing problems getting totem to play flash video files (or indeed any other types of media files) - you can fix this by installing the package **ubuntu-restricted-extras**.  Open a terminal and type in the command:

```
sudo apt-get install ubuntu-restricted-extras
```

The package manager will tell you that it also wants to install a whole slew of stuff.  Tell it "yes" (by hitting "y" I think).  This will install to your system a bunch of codecs, which will enable it to play pretty much any media file.

Of course, the best thing to do is to use **vlc**, as recommended by lotsa folk in this thread.  vlc is grrreat.  I have yet to find a media filetype it can't handle.  Though this may be down to the fact that I also have ubuntu-restricted-extras and w32codecs.

---

### Post by jwaclawsky on 2009-04-28
I am still a little new to Linux. You say that Nautilus is the default ubuntu file browser. But Where do I find it?.My package manager (synaptic) says Nautilus is installed (somewhere)? On my tool bar I have Applications, Places and System. I clicked through everything there but what should I be looking for?

---

### Post by MysticGold04 on 2009-04-28
If you go to places > home folder... the window that comes up is the file manager (Nautilus)

---

### Post by jwaclawsky on 2009-04-28
Go it thanks!   :-)

---

### Post by meka4996 on 2009-05-23
this would be more comprehensive ...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

