---
title: "Is a command line only system possible?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by cavedog on 2009-01-17
I have a old desktop,IBM something with  AMD-K6-2, 500 MHz, 256Meg RAM, 8Meg video card.  I have tried Xubuntu on this machine, but it still runs slow, especially when accessing the InterTube.  I'm wondering if a command line only system would be possible, and / or better.  I'm an old DOS dog from the days of BBS's, and I don't have problems learning the commands, if it is a viable option. My research tells me that there are things that I have to be able to do from the command line.  My questions is, can I do EVERYTHING from the command line?

---

### Post by sleepyjon on 2009-01-17
Yes it is, just download the server version. You can even use links for a browser.

---

### Post by Muffinabus on 2009-01-17
Yeah, if I'm not mistaken there are even some text based web browsers and audio players.

---

### Post by HermanAB on 2009-01-17
No need to download anything.  Just do:

$ sudo init 3

Cheers,

Herman

---

### Post by ushimitsudoki on 2009-01-17
Yes, of course this is possible.

I have a media player/browser/multiple screens all that jibber-jabber from the command line on my laptop.

No Flash in the browser, though!

---

### Post by m_duck on 2009-01-17
If you're starting again, download the alternate install CD, then after selecting your language on the first menu, press F4, select "Install a command line system" then "Install Ubuntu".

---

### Post by kerry_s on 2009-01-17
try arch, i have a t20 700mhz 128mb ram, i'm using jwm for my window manager, pcmanfm filemanager, leafpad text editor, firefox.....

[ftp://ftp.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/latest/archlinux-2008.06-core-i686.iso](ftp://ftp.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/latest/archlinux-2008.06-core-i686.iso)

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

if you that gui won't load bug, add:
Option "BusType" "PCI"

to the vid driver section.

i'm not going to recommend debian because they keep dropping firmware, so you'll end up fighting to get sound working. arch is the fastest lowest resource alternative i've found and i tried many. i got debian on my vaio 450mhz 256mb ram, but i'll be moving that to arch eventually.

---

### Post by cavedog on 2009-01-17
> **m_duck said:**
> If you're starting again, download the alternate install CD, then after selecting your language on the first menu, press F4, select "Install a command line system" then "Install Ubuntu".

That's where I'm at.  I'm almost at the spot in the Installation / Low Memory System How To where it goes over the GUI's, and I'm thinking, "I used to do everything from the command prompt."

---

### Post by chriscross93 on 2009-01-17
Here is yet another solution, but it is easy to "turn the GUI back on" if you ever want to.

1. Install Ubuntu normally
2. Goto ```
System -> Administration -> Services
```
3. disable the ```
Graphical Login Manager (GDM)
``` service
4. If you ever need to turn the GUI back on run this code
```
sudo /etc/init.d/gdm start
```



good to go.:guitar:

---

### Post by sleepyjon on 2009-01-17
> **chriscross93 said:**
> Here is yet another solution, but it is easy to "turn the GUI back on" if you ever want to.

1. Install Ubuntu normally
2. Goto ```
System -> Administration -> Services
```
3. disable the ```
Graphical Login Manager (GDM)
``` service
4. If you ever need to turn the GUI back on run this code
```
sudo /etc/init.d/gdm start
```



good to go.:guitar:

Yeah, that's probably the most obvious and best solution.

---

### Post by bhadotia on 2009-01-18
> **kerry_s said:**
> try arch, i have a t20 700mhz 128mb ram, i'm using jwm for my window manager, pcmanfm filemanager, leafpad text editor, firefox.....

[ftp://ftp.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/latest/archlinux-2008.06-core-i686.iso](ftp://ftp.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/latest/archlinux-2008.06-core-i686.iso)

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

if you that gui won't load bug, add:
Option "BusType" "PCI"

to the vid driver section.

i'm not going to recommend debian because they keep dropping firmware, so you'll end up fighting to get sound working. arch is the fastest lowest resource alternative i've found and i tried many. i got debian on my vaio 450mhz 256mb ram, but i'll be moving that to arch eventually.

+ 1 for Arch.
Some of its features include:
[LIST=1]
[*]i686 optimized packages
[*]A super fast package manager.
[*]Complete control over the OS
[*]Complete documentation on wiki
[*]Rolling release model - you never have to download a whole distro to upgrade.
[/LIST]

---

### Post by solitaire on 2009-01-18
Just wondering since you can play music and visit some web pages using the command line....

Can you play video in the command line with no Display Manager (i.e. GDM is stopped) running? ;)
if it defaults to full screen could it be possible :D

---

### Post by blackened on 2009-01-18
Anything with fluxbox, icewm, etc. should run fine on that machine. Have you tried Puppy Linux, Damn Small Linux, or just installing fluxbox on Ubuntu? All are viable solutions.

---

### Post by cavedog on 2009-01-18
> **blackened said:**
> Anything with fluxbox, icewm, etc. should run fine on that machine. Have you tried Puppy Linux, Damn Small Linux, or just installing fluxbox on Ubuntu? All are viable solutions.

I've tried Puppy, but not DSL.  Is it possible to install fluxbox onto an existing xubuntu installation, and either replace the xfce or be able to toggle back and forth between them?

---

### Post by blackened on 2009-01-18
> **cavedog said:**
> ...Is it possible to install fluxbox onto an existing xubuntu installation, and either replace the xfce or be able to toggle back and forth between them?

Absolutely. Once you install fluxbox it will be selectable in the "Session" menu in XDM.

---

### Post by cavedog on 2009-01-18
I thought so.  I'll give that a shot.  And there is always the "Disable the Graphical Login Manager" tip that chriscross provided.

Thanks to all.  This should be enough to keep me in glorious geekdom for a week or so.

---

### Post by bhadotia on 2009-01-18
> **cavedog said:**
> I thought so.  I'll give that a shot.  And there is always the "Disable the Graphical Login Manager" tip that chriscross provided.

Thanks to all.  This should be enough to keep me in glorious geekdom for a week or so.

Openbox is better than flux box in my opinion ([Here's a guide]("http://wiki.archlinux.org/index.php/Openbox")).

---

### Post by revertTS on 2009-03-10
> **solitaire said:**
> Just wondering since you can play music and visit some web pages using the command line....

Can you play video in the command line with no Display Manager (i.e. GDM is stopped) running? ;)
if it defaults to full screen could it be possible :D

This is possible with mplayer if you compile it with framebuffer support.

---

