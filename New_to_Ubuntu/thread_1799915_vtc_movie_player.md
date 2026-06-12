---
title: "vtc movie player"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Old-un on 2011-07-08
I would like to learn more about Linux in general and so i have been trying to run free demo's by Marrutt Software Training prior to purchase but all i get is a black screen? Is there anyway i can get to run these free demo's? Someone did mention vtc media player but i can't find it in either Synaptic or the Ubuntu Software Centre?

---

### Post by OldBoy44 on 2011-07-08
Do you mean the VLC Player, which is in the Software Center ?  :)

---

### Post by coffeecat on 2011-07-08
> **Old-un said:**
> Someone did mention vtc media player but i can't find it in either Synaptic or the Ubuntu Software Centre?

That's because it's V**L**C. **V**ideo**L**an **C**lient. It should be there. :)

---

### Post by nomko on 2011-07-08
You mean Vlc media player? Than can be found in synaptic. Vlc should play almost every mediatype without extra plugins (i.e.: plugins for wmf media format)
 
Did you install:
ubuntu-restricted-extras
 
From medibuntu ([http://medibuntu.org/](http://medibuntu.org/)):
w32codecs (for 32-bit ubuntu version)
w64codecs (for 64-bit ubuntu version)
libdvdcss2
non-free-codecs

---

### Post by Old-un on 2011-07-08
I have installed VLC movie player and i have added the Medibuntu repositories + i also added W32 codecs, libdvdcss2, and non-free-codecs and still i can't get the free demo's to run?

---

### Post by coffeecat on 2011-07-08
What type of files are they? Right-click on one -> Properties -> Audio/Video tab. Does it say anything about audio and video codecs?

---

### Post by mc4man on 2011-07-08
No - it is actually VTC player, I know there's some threads around here concerning this, try a google site search ect, (forget the outcome

---

### Post by Zill on 2011-07-08
> **mc4man said:**
> No - it is actually VTC player...
Looks like VTC player is part of [Adobe Air]("http://www.adobe.com/cfusion/marketplace/index.cfm?event=marketplace.offering&marketplaceid=1&offeringid=10058") and a linux version is apparently available - no idea how good it is though. :|

---

### Post by AlphaNeil on 2011-07-08
Marrutt tutorial videos are in Quicktime format. The files are .mov files.

---

### Post by Zill on 2011-07-08
> **Old-un said:**
> I would like to learn more about Linux in general and so i have been trying to run free demo's by Marrutt Software Training prior to purchase...
While I fully understand your wish to learn more about Linux you may find these kind of commercial tutorials are of limited use as they are unlikely to be kept updated with the rapid changes in Linux distros and applications.

My suggestion is to spend (some of) the cost of these tutorials on a cheap used PC and then stick as many Linux distros as you like on it.  There are lots of PCs available for peanuts, generally because Windows has ground to a halt. ;-)

If you leave your primary PC untouched, you can then experiment with your "secondary" PC and, if you manage to break it you can then have the delights of fixing it, learning as you go.

There is tons of information available on this website and in the wider community.  Of course, if you hit any problems you can't solve yourself just post on these forums for a quick(!) answer.

---

### Post by mc4man on 2011-07-08
In any event - it would seem that some (or all ?) of these files are .mov with an encoding of smc (?)
If so then mplayer, (frontend of smplayer or umplayer) should work, xine based players may also be good. 
vlc and gnome based players will not work so well
screen shows info on 1, plays fine in mplayer and an install of totem-xine I've keep alive (totem-xine was dropped some time ago

---

### Post by Old-un on 2011-07-08
Have now got VTC player up and running. Big thanks to everyone for their help.

---

