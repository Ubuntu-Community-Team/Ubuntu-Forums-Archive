---
title: "Ubuntu and libre.fm"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by bananabob on 2009-04-27
I am trying to use libre.fm <http://libre.fm>
I have tried both Amarok 1.4.9 and Banshee 1.4.3.
I can get neither of them to work with libre.fm <http://libre.fm>
There seem to be several reports of Amarok 1.4 working, that is why I thought I would try Banshee.
The instruction from libre.fm is to add the following to your etc/hosts file

    89.16.177.55 post.audioscrobbler.com

Here are the results from a ping
    $ ping post.audioscrobbler.com 
    PING post.audioscrobbler.com 
    (89.16.177.55) 56(84) bytes of data.
    <snip ....... removed lines>
    --- post.audioscrobbler.com 
    statistics ---
    9 packets transmitted, 8 received, 11% packet loss, time 8003ms
    rtt min/avg/max/mdev = 298.244/302.058/311.563/4.152 ms

When I use Firefox to go to [http://www.audioscrobbler.net/](http://www.audioscrobbler.net/) I am taken to there instead of the libre.fm site
However if I set Firefox to use "No Proxy" instead of "Use System Proxy Settings" I get to the site I want.
I assume that both Amarok and Banshee are going to the wrong site becasue of some "system proxy" That I do not know about.
Can I get some help here please.

---

### Post by llamabr on 2009-04-27
Are you able to listen via firefox?

---

### Post by bananabob on 2009-04-27
Sorry I didn't make myself clear. This is about scrobbling not listening. libre.fm is a free replacement for last.fm, and I need to scrobble to it rather than last.fm.

---

### Post by mantisdolphin on 2009-07-03
Any results with libre.fm?  I'm trying to transfer a profile from Last.fm to Libre.fm and am not having success.  

I'm using instructions from [http://bugs.libre.fm/wiki/Using_lastscrape]("http://bugs.libre.fm/wiki/Using_lastscrape").

---

### Post by bananabob on 2009-07-03
I had some problems with the Beautuiful soup in the repositories so I downloaded used the 3.0.7a instead. It worked fine.

---

### Post by bananabob on 2009-07-03
I should also add that there is now a plugin for Amarok 1.4 available from [http://ebanana.orconhosting.net.nz/librefm.html](http://ebanana.orconhosting.net.nz/librefm.html)

---

### Post by mantisdolphin on 2009-07-04
I did the -a version.  I'll have to step back through the instructions.  

I'm hoping there'll be a Banshee plugin.  Should check the Banshee forums for news.

---

### Post by DouglasAWh on 2011-03-23
> **mantisdolphin said:**
> 
I'm hoping there'll be a Banshee plugin.  Should check the Banshee forums for news.

Any update on this? As far as I can tell, there's still no plugin: [https://bugzilla.gnome.org/show_bug.cgi?id=579801](https://bugzilla.gnome.org/show_bug.cgi?id=579801)

---

