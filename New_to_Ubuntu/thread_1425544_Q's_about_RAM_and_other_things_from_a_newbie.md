---
title: "Q's about RAM and other things from a newbie"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by superstargoddess on 2010-03-09
Brand new to any Linux product, installed Ubuntu yesterday.  I'm very good with computers, built my own and have no problem fixing anything that needs fixed in Windows.  However, I have a few questions about Ubuntu since it's been driving me nuts!  A little difficult to get used to even though I'm sure that since this is the most user friendly version that it must be way hard in a basic distro!

First of all, just noticed that even though I am just sitting here with Firefox open and nothing else, that my ram usage is 42%, which boggles my mind.  I have 4gigs of ram but it only recognizes 3.1gig of it apparently, and this is a 64 bit system and distro.  (someone can also tell me how to fix that if they like!)  Nothing else too special going on, I've changed my UI and that's about it.  Ubuntu One thingee is running in the system tray, and Pidgin, but that's about it.  Besides the screenlets which I have a few little things going on there.  So basically, why is this taking up so much RAM?

Also, I've been struggling with themes sometimes, trying to get them installed.  Seems that no matter what I do, they won't install when I drag and drop them in various forms.  I'm pretty much getting that all figured out though.  Still having problems with conky though, but I'll also work that out I'm sure.

Installing packages that I download is a bit hectic as well.  Seems that most things don't show up in my applications list or wherever after installed so I have to go track them down.  And it's difficult for me to install things that I download without it being in the package manager thingee.  It's like I don't know how to install them but I have been finding commands on how to do that.

I've spent a lot of time on Google recently figuring everything out!  It's a lot different than anything else I've ever seen before and I love it.  I have it pretty tricked out appearance wise and it's just beautiful right now.  I'm just a little concerned about the RAM thing, that's about it.  Everything else I can figure out on my own, but you can comment on those other things if you like.

I'm about ready to try to resize my partitions, move over some basic things like pics, mp3's, and movies, and go ahead and get rid of Windows and use the other partitions as storage space.  I know I probably don't need to do this with Ubuntu, but with Windows I always kept 2 or 3 partitions in case the OS got messed up and I had to reinstall.  Then all my other crap would be safe on the other partitions.  :)

But thanks in advance for the help, and I tried to do a search about the RAM thing but didn't find anything.  Seems like most of the things I look for aren't quite covered in threads that I find!  ><

---

### Post by tom4everitt on 2010-03-09
gnome-system-monitor is a nice little utility to figure out who is eating your ram. Launch it from a terminal with:

gnome-system-monitor 

Another useful command that you can use in the terminal is 

top

which does pretty much the same thing but doesn't require a gui. 


Good luck, seems like you're on the right track!


EDIT: And yes, software installation is a bit awkward in the beginning, although its just matter of time until you prefer the linux way. /usr/bin and /usr/local/bin is the normal installation folders for programs (if you didn't notice that already). Generally its good habit to use apt-get or aptitude (or synaptic) to install applications, its very fast and convenient. And getting the hang of the terminal is very useful!

---

### Post by halitech on 2010-03-09
welcome to Ubuntu and the forums :)

are you sure you downloaded and installed the 64bit version of ubuntu? 64bit *should* show you around 3.9gig where the 32bit normally shows around 3.1 of 4 gig of ram.

Installing packages should be easy. Open Synaptic, find the program you want to install, mark it (right click - install) and then click apply. They should show up in the menu under whatever category they fit into.

As long as you installed with a seperate /home partition then you *shouldn't* need a backup partition but backing up data is always a good idea to another drive or media.

---

### Post by thatguruguy on 2010-03-09
> **superstargoddess said:**
> I have 4gigs of ram but it only recognizes 3.1gig of it apparently, and this is a 64 bit system and distro.  (someone can also tell me how to fix that if they like!)

Could you run the following commands in the terminal, and post the results here?

```
free -m
```

```
uname -m
```

```
cat /proc/version
```

```
file /sbin/init
```

---

### Post by superstargoddess on 2010-03-09
> **thatguruguy said:**
> Could you run the following commands in the terminal, and post the results here?

```
free -m
``````
uname -m
``````
cat /proc/version
``````
file /sbin/init
```

1. total       used       free     shared    buffers     cached
Mem:          3145       2443        702          0        328        685
-/+ buffers/cache:       1429       1715
Swap:         3008         34       2973

2. x86_64

3. Linux version 2.6.31-20-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010

4. /sbin/init: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

I downloaded the Ultimate Edition Ubuntu if that makes any difference.  I figured that I wanted something that had a good start to it.  But if I should install something a bit more tamed down and then just build on it, let me know.

Thank you to the others as well!  It seems that on this sys monitor that is in my screenlet that it isn't showing anything that it taking up a lot of resources.

---

### Post by qyot27 on 2010-03-09
> **superstargoddess said:**
> Installing packages that I download is a bit hectic as well.  Seems that most things don't show up in my applications list or wherever after installed so I have to go track them down.  And it's difficult for me to install things that I download without it being in the package manager thingee.  It's like I don't know how to install them but I have been finding commands on how to do that.
If it's a .deb package, just double-click on it.  That'll bring up Gdebi, and you'll be able to click Install Package.

If it's a binary or source code, it gets trickier because there are multiple ways of handling it.  You could copy the binary to /usr/bin or /usr/local/bin, you could put it in its own directory and then add that directory to the $PATH variable, or you could eschew those things and always remember to put a ./ in front of the app name when you run it.  For source code, you'd have to find the compilation instructions first.  
```
./configure
make
sudo make install
```
or some variant of that process is common, but not universal.  It also depends on where exactly you're installing to (which dictates whether or not you use sudo on the make install step), or you could use checkinstall, which builds a .deb package for you and installs that so it shows up in Synaptic.  There are pluses and minuses to both ways.

---

### Post by psusi on 2010-03-09
Looks like you have hardly any ram being used at all.  2.4 gigs free with another 685 megs in the cache.  As for why it only sees 3.1 gigs, post the output of the dmesg command.

---

### Post by audiomick on 2010-03-09
No, 2.4GB used, 702MB free. Are you using a video card that shares the RAM, maybe?

---

### Post by psusi on 2010-03-09
Doh... darn forums and their whitespace munching... my eyes didn't parse that correctly with the alignment broken.  Yea, one of those crappy on board video controllers that steals system ram could account for why only 3.1 gigs is seen.  Well, if it were set to use a 512 meg video buffer.

---

### Post by superstargoddess on 2010-03-09
> **audiomick said:**
> No, 2.4GB used, 702MB free. Are you using a video card that shares the RAM, maybe?

Using a good ATI Radeon card.  Didn't have an issue with it on Windows.  Still not sure what's going on. Up to ram usage of 47% now.  ><

---

### Post by audiomick on 2010-03-09
> **superstargoddess said:**
> Using a good ATI Radeon card.  Didn't have an issue with it on Windows.  Still not sure what's going on. [COLOR=Red]Up to ram usage of 47% now[/COLOR].  ><
Don't worry too much about it growing. Linux accumulates RAM as Cache, but that is not a problem.
It just occurred to me; maybe you would like to read this
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by mbzn on 2010-03-09
Good article in the previous post. If you go Applications>System Tools>HTOP which is top with colour you will notice near the top of the screen/window Mem, green is USED, blue and yellow is buffers and ??? (used but still available if needed). This boosts performance somewhat. You'll start worrying if it starts eating swap under no load. I only have 2 GiB ram on UE64(2.5), so i'm unable to help with the 3.1GiB issue.

By the way UE is still the standard Ubuntu with 100's of packages(some of which you'll never use and some you cant go without).

Good luck.

---

### Post by superstargoddess on 2010-03-09
> **audiomick said:**
> Don't worry too much about it growing. Linux accumulates RAM as Cache, but that is not a problem.
It just occurred to me; maybe you would like to read this
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

Oh I see, so instead of having 320 available right now, I have 1632 from what that site says.

Also, on the HTOP, it says that I have a bunch of firefox open and it says new tab and then some site that I haven't had open for a long time. I think that I will try to kill those processes and see what happens.

Thanks so much to everyone so far!  This community is awesome!

Edit: And yeah, I'm starting to wonder about UE and if I have too much crap.  A lot of this crap I don't even know what it is or think that I want it!

---

### Post by superstargoddess on 2010-03-11
After much contemplation and reading, I decided to get rid of Ultimate Edition Ubuntu today and get Linux Mint... and I love it!  (just to keep you updated)  :P

---

