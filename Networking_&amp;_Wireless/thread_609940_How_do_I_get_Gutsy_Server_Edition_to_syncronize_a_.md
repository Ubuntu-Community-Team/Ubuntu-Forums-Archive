---
title: "How do I get Gutsy Server Edition to syncronize a folder with my Gutsy desktop?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Jason.TJ.Johnson on 2007-11-11
Ok, here's the deal.

I have two computers that I'm trying to work with.

I have an older P3 computer with 256MB ram. That computer is sitting in my closet. It has Ubuntu Gutsy Server Edition installed along with LAMP. I use it to host a jinzora installation so I can access my music collection anywhere I have access.

I got everything working fine with that. I copied my music collection from my desktop hard drive to the hard drive in the server computer. Problem is, when I purchase new albums and rip them to my collection, I have to manually update the collection on my desktop as well as the collection on the server. How can I get my server to synchronize with my desktop machine so all I have to do is keep one updated?

On a side note, I have Jinzora set up to automatically check the folders to see if there's any changes, and that works fine, but I want the server to check my desktop to keep itself updated.

---

### Post by scorp123 on 2007-11-11
There are solutions out there which can do this .... Probably the easiest ("easy" as in: not so much to install and not so many dependencies involved) for you would be to e.g. create a "cron" job that will automatically run a "rsync" between your two machines in regular intervals (e.g. every two hours?). Advantage here: "rsync" is command-line only, so yes, it can easily be scripted and automated.

Similar to this would be "unison". That's a nice program with a somewhat nice GUI frontend and it too can keep two folders or two computers synced. If you google around you may find some good tutorials.

The most sophisticated solution and at the same time most likely the most difficult one to get up and running (it involves tons of dependencies!) is Novell's iFolder. That's a really neat solution IF you can get it running. You just right-click on a folder and then tell your Nautilus file manager to share it via iFolder .... And voila, the folder automagically syncs with your iFolder server. The cool thing is that other client computers can subscribe to those shares too and e.g. contribute to your file shares. More infos: [http://www.ifolder.com](http://www.ifolder.com)

There also is this "iFolder How To" for Ubuntu ... no idea if it will still work:
[https://help.ubuntu.com/community/iFolder](https://help.ubuntu.com/community/iFolder)

---

### Post by Jason.TJ.Johnson on 2007-11-11
Awesome!
I didn't expect such a quick response, but damnit I love it!

Anyhow, I'm going to see if I can do the ifolder first. I'll let you know how it goes, thanks!

---

### Post by Jason.TJ.Johnson on 2007-11-11
:(
The ifolder website isn't loading for me, and the domain (which shows an IP of 64.14.94.162 using ping) doesn't respond to my pings.

Guess I'll have to use an alternative option.

---

### Post by kevdog on 2007-11-11
Ive used unison, its OK however sometimes it hangs -- not sure if its unison or the connection.  Id like to try ifolder but it seems like the links are dead.

---

