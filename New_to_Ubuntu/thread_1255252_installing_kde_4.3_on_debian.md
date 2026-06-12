---
title: "installing kde 4.3 on debian"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by nikhilbhardwaj on 2009-09-01
i have always liked kde 
and the reviews kde 4.3 has got have convinced me to try it

i want to install it on debian prefrably
i've got a net install image and will install that, then i'd like to install kde 4.3 and other stuff like multimedia etc
i've found repositories online for the multimedia and other stuff
but can't seem to find one for kde 4.3

could someone help me out with this


if it is not possible to install kde 4.3 on lenny
then i'd like to install it on ubuntu 9.04 ( net install because it's a pin to remove all things that you don't need )

but debian is the first choice

plz hurry
i'll start the installation as soon as i find the answer to these questions

---

### Post by mdmarmer on 2009-09-01
You should install antix or Mepis.  Then you can use the smxi script to add or upgrade KDE to 4.3.  Mepis is a lightweight derivative of Mepis.

look here:  [http://www.mepislovers.org](http://www.mepislovers.org)
[http://antix.freeforums.org](http://antix.freeforums.org)
[http://www.mepis.org](http://www.mepis.org)
[http://techpatterns.com](http://techpatterns.com) (for more info on smxi script)
[http://www.sidux-underground.com](http://www.sidux-underground.com)

You'll find threads in these forums about users who have remastered Mepis with KDE 4, what repositories to use, and so on.  If you dist-upgrade with testing repositories enabled (antix ships that way) you'll get a fairly new version of KDE.  Note that antix ships with xfce and fluxbox (no KDE, but that's easy to add with smxi script), and Mepis ships with KDE 3.5 (could be upgraded to KDE 4)

In this thread there is a link to a user-remastered .iso of Mepis with KDE 4.3 [http://mepislovers.org/forums/showthread.php?t=22158](http://mepislovers.org/forums/showthread.php?t=22158)
He has set up a forum at [http://danumlinux.com/](http://danumlinux.com/)

If you want to start with the net install of Debian, the smxi script will make it fairly easy to configure it however you want to.  The easiest and best path is to start with the remaster above.


Mike

---

### Post by jjgomera on 2009-09-01
kde 4.3 is in debian sid, so you can install lenny and doing [apt-pining]("http://wiki.debian.org/AptPinning") to install kde 4.3 from sid repo

---

### Post by snowpine on 2009-09-01
sidux is Debian Sid (unstable) with KDE 4 ready to go out-of-the box:

[http://sidux.com/](http://sidux.com/)

It is a fun, fast, and up-to-date Debian-based distro.

Debian Lenny is the "stable" branch, which means its software is old. (Kind of like using Ubuntu 8.04.) I believe Lenny uses KDE 3.5.

---

### Post by cascade9 on 2009-09-01
> **nikhilbhardwaj said:**
> i have always liked kde 
and the reviews kde 4.3 has got have convinced me to try it

i want to install it on debian prefrably

Debian Sid has the newest version of KDE 4.3 (newer than any released version) 

Sidux is still KDE 4.2

---

### Post by sandyd on 2009-09-01
for ubuntu, you need
[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

---

### Post by snowpine on 2009-09-01
> **cascade9 said:**
> Debian Sid has the newest version of KDE 4.3 (newer than any released version) 

Sidux is still KDE 4.2

Sidux *is* Sid... KDE 4.3 came through a few weeks ago: [http://sidux.com/PNphpBB2-viewtopic-t-17421.html](http://sidux.com/PNphpBB2-viewtopic-t-17421.html)

---

### Post by nikhilbhardwaj on 2009-09-01
this is the first time i've ever heard of apt-pinning
should i go ahead with it

i'm compiling the kernel now
and after that will give it a shot
hopefully it won't do any harm

one more thing which one of sid's repo's should i add

---

### Post by snowpine on 2009-09-01
> **nikhilbhardwaj said:**
> this is the first time i've ever heard of apt-pinning
should i go ahead with it

i'm compiling the kernel now
and after that will give it a shot
hopefully it won't do any harm

one more thing which one of sid's repo's should i add

You should not use apt-pinning in this situation. Please don't mix Stable and Unstable (it is okay to mix Testing and Unstable).

For Debian Stable, the equivalent is Backports: [http://backports.org/dokuwiki/doku.php](http://backports.org/dokuwiki/doku.php)

But you will not find KDE 4.3 in Lenny Backports... it only entered Unstable less than a month ago!

Bottom line: if you want the latest software, don't use Stable.

---

### Post by jjgomera on 2009-09-01
> **nikhilbhardwaj said:**
> this is the first time i've ever heard of apt-pinning
should i go ahead with it

i'm compiling the kernel now
and after that will give it a shot
hopefully it won't do any harm

one more thing which one of sid's repo's should i add

[http://forums.debian.net/viewtopic.php?f=6&t=43702](http://forums.debian.net/viewtopic.php?f=6&t=43702)

really only you want, kde-full, kde-minimal, whatever complete you like kde, dont worry about libraries, apt may resolve

If you dont want use pinning (really is the best solution to have any actualization in kde from sid), you can change repos to sid, install kde and go back repos to lenny.

---

### Post by nikhilbhardwaj on 2009-09-02
> **snowpine said:**
> You should not use apt-pinning in this situation. Please don't mix Stable and Unstable (it is okay to mix Testing and Unstable).

For Debian Stable, the equivalent is Backports: [http://backports.org/dokuwiki/doku.php](http://backports.org/dokuwiki/doku.php)

But you will not find KDE 4.3 in Lenny Backports... it only entered Unstable less than a month ago!

Bottom line: if you want the latest software, don't use Stable.

i tend to agree with you
the apt pining page said that it wasn't the best method

but i'll give it a try once
and if it doesn't work then probably i'll move to sid

---

