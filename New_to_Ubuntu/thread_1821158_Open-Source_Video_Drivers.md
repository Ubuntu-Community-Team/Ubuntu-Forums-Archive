---
title: "Open-Source Video Drivers?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by travisHAZE on 2011-08-08
:popcorn:Grab some popcorn, it's a read (or skip below)


     Running 11.04 (Natty) from fresh install using Ubuntu's standard video drivers. These drivers are stable enough for the most basic tasks (and I know it's driver related), but anything involving even semi-complex graphical power causes the computer to sputter, lag, and eventually locks up (and a a brutal restart is necessary.) Unity included (timed average is about 6hrs to crash for Unity) so I've switched to GNOME (Ubuntu Classic (No Effects)) and that stops the timed crashing scenario (and honestly I like GNOME more, so it's not a hassle).
     Now for the short time I've been running Linux, I've enjoyed myself despite some hassles with it, some have been fixed thanks to google, and will continue to use it (I'm aware its more of a my computer thing than Ubuntu so dev team I'm not yelling and screaming). However, my integrated Radeon XPRESS 200M has a little bit more power than Ubuntu is letting it have and I managed to install the proprietary drivers even though cchtml.com said FGLRX wouldn't work with my video card. Everything seemed to run better, but I wasn't absolutely certain, I ran Unity as my desktop, never crashed, flash applications ran better (videos and games, no stuttering). HOWEVER aticonfig was not present as a command in my terminal, I had no xorg.conf file (and I've never have one).

(And even now, every time I go down a line, it will go back and forth between graphical errors in the screen and being completely fine.)



**The Gist** (Skip Here)
Toshiba Satellite A135-S2326
ATI Radeon XPRESS 200M
With just Ubuntu standard video drivers, graphically my computer is unstable (but functional)
Installed proprietary drivers for ATI (via instructions found [here]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx")) even though they said my card wouldn't work.
Everything functioned better (no instability issues apparent)
However I still had no xorg.conf file, aticonfig wasn't present as a command in the terminal (so xorg could be generated)
The same website listed above claimed I would need open-source drivers, which suggested Ubuntu-X? Reading the website I couldn't find anything that would make any sense to me, so I'm turning here. Advice, tips?


Thank you in advanced,
Travis

---

### Post by beew on 2011-08-08
The open source graphic drivers that come with ubuntu are outdated and buggy(as you don't get any bug fix). If you seriously want to give open source drivers  a try add the xorg-edgers ppa and upgrade your drivers. 

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

I am using them in a test install in an external drive which I boot off a few machines with nvidia and Ati cards, the open drivers are quite usable actually, I can watch hd and 3d movies and I have full 3d desktop effects, no random lock up or freezing . The improvements over the default Ubuntu offer are quite spectacular.

---

### Post by travisHAZE on 2011-08-08
That's the Bleeding Edge Repository right?

---

### Post by sandyd on 2011-08-08
> **travisHAZE said:**
> That's the Bleeding Edge Repository right?

Correct. This is directly from Git.

I use them (well, I don't use Ubuntu, but I use bleeding edge mesa/gallium drivers, along with bleeding edge ati, libdrm...), and they work wonders compared to the ones that are shipped by default.

If you want more stable...

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


Make sure you install ppa-purge beforehand btw, so that if it breaks, you can always go back.

---

