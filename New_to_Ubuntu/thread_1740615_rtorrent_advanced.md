---
title: "rtorrent advanced"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by junkyhlm on 2011-04-27
I use rtorrent to download torrents on my server and then play them on my XBMC HTPC setup. When XBMC isn't as configurable as i desire i would like to make a rtorrent script to move my files into a XBMC friendly catalogue tree.

Lets say i download  <custom name> to the folder:
/media/store/download
and when the download is finished rtorrent (via .rtorrent.rc) moves the file to:
/media/XBMC
and rtorrent continues to seed, so far so good.

When the download is finished i would like to move the files to:
/media/XBMC/<custom name> without having a watched dir for every <custom name>
 
So to my script:
I would like a script that matches the series name with a regexp for example and moves the files to the correct catalogue.

ex.
If the script finds *junkyhlm* in the file/catalogue name it will move the files to /media/XBMC/junkyhlm (provided that the folder /media/XBMC/junkyhlm exsists, otherwise it put the files in /media/XBMC)
and so on..

How to get this script to work and how to get rtorrent to understand the move and continue to seed afterwards.

---

### Post by matthew.parlette on 2011-04-27
> **junkyhlm said:**
> 
So to my script:
I would like a script that matches the series name with a regexp for example and moves the files to the correct catalogue.

ex.
If the script finds *junkyhlm* in the file/catalogue name it will move the files to /media/XBMC/junkyhlm (provided that the folder /media/XBMC/junkyhlm exsists, otherwise it put the files in /media/XBMC)
and so on..

I've been very interested in getting something like this together too, but I just haven't thought of a good solution yet. Maybe have a file of learned show/movie names and a file of learned tags, so that everything else can be stripped from the filename so it is a clean file I am putting into my library.

I have put a good bit of thought into this, but haven't really discovered a solution yet (or haven't coded it yet, I should say). But I did stumble across someone suggesting to use the XBMC scrapers to get the show/movie information, which sounds much more promising. I haven't looked any more into using this from a script, so it may not even be possible...actually I can't seem to find that link that mentions this. But I found this which may be promising: [http://netbl0g.blogspot.com/2009/11/rtorrent-xbmc-tv-library.html]("http://netbl0g.blogspot.com/2009/11/rtorrent-xbmc-tv-library.html"). Let me know what you find, and I'll do the same as I look for a solution.

> **junkyhlm said:**
> How to get this script to work and how to get rtorrent to understand the move and continue to seed afterwards.

I don't think this is possible, at least from what I've seen. Once the files are moved, rtorrent doesn't know about that and can't seed

---

### Post by junkyhlm on 2011-04-27
> **matthew.parlette said:**
> 
I don't think this is possible, at least from what I've seen. Once the files are moved, rtorrent doesn't know about that and can't seed
 
You can move the files with execute=mv... etc.. but i want it to be more dynamic. Will look into that link you posted when i get home. Looks promising anyway. Thank you.

---

### Post by matthew.parlette on 2011-04-27
> **junkyhlm said:**
> You can move the files with execute=mv...

Agreed, but I mean that once you move the files, rtorrent doesn't keep track of them and you can no longer seed that torrent.

---

### Post by pyroscope on 2011-04-27
[https://pastee.org/8q8bt](https://pastee.org/8q8bt) and use the -c and -s options, resulting in this structure:

/foo/XBMC/Bar/bar.s01e01.avi => /foo/Downloads/Completed/bar.s01e01.avi

In other words, create a scraper-friendly tree for XBMC, and keep the downloads physically where they are, so rTorrent can still seed them. Or use FlexGet and wait till I finished the rtorrent plugin that'll set custom fields based on the info in FlexGet (series, episode number, etc.), which can then be used in classic completion moving. Neither of these needs any special watchdirs.

---

### Post by junkyhlm on 2011-04-28
> **matthew.parlette said:**
> Agreed, but I mean that once you move the files, rtorrent doesn't keep track of them and you can no longer seed that torrent.
 
My current setup is one watched dir per download type and an automatic move with execute=mv... that rtorrent understand and seeds from, no problem what so ever.

---

### Post by junkyhlm on 2011-04-29
> **matthew.parlette said:**
> I've been very interested in getting something like this together too, but I just haven't thought of a good solution yet. Maybe have a file of learned show/movie names and a file of learned tags, so that everything else can be stripped from the filename so it is a clean file I am putting into my library.
 
I have put a good bit of thought into this, but haven't really discovered a solution yet (or haven't coded it yet, I should say). But I did stumble across someone suggesting to use the XBMC scrapers to get the show/movie information, which sounds much more promising. I haven't looked any more into using this from a script, so it may not even be possible...actually I can't seem to find that link that mentions this. But I found this which may be promising: [http://netbl0g.blogspot.com/2009/11/rtorrent-xbmc-tv-library.html](http://netbl0g.blogspot.com/2009/11/rtorrent-xbmc-tv-library.html). Let me know what you find, and I'll do the same as I look for a solution.
 
 
 
I don't think this is possible, at least from what I've seen. Once the files are moved, rtorrent doesn't know about that and can't seed
 
 
I have tried the tip you posted but i just cant get it to work, i think the author left some valuable information out of the picture sadly :/

---

### Post by junkyhlm on 2011-04-29
Is there anyone who have been laborating with this, i will gladly beta test scripts for learning purposes.

---

### Post by pyroscope on 2011-04-29
> **junkyhlm said:**
> Is there anyone who have been laborating with this, i will gladly beta test scripts for learning purposes.
See the link to a script in the post above, and also [http://code.google.com/p/pyroscope/wiki/FlexGetPlugins](http://code.google.com/p/pyroscope/wiki/FlexGetPlugins) (which will be probably working soon, i.e. this weekend), in case you use FlexGet.

---

### Post by junkyhlm on 2011-05-02
> **pyroscope said:**
> See the link to a script in the post above, and also [http://code.google.com/p/pyroscope/wiki/FlexGetPlugins](http://code.google.com/p/pyroscope/wiki/FlexGetPlugins) (which will be probably working soon, i.e. this weekend), in case you use FlexGet.
 
Thank you i'll try your script (both of them) on a virtual machine to se if it works :)
 
EDIT:
This type of solution is not what im looking for. I would like for the files to be moved physically with bash-scripting only no additional programs. I'm sure that your solution is great for you but it doesnt help me sadly :/

---

