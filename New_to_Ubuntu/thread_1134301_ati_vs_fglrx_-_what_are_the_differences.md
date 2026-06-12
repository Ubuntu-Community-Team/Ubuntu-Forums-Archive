---
title: "ati vs fglrx - what are the differences?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by usererror on 2009-04-23
I just upgraded to 9.04 from 8.10. I was having odd video playback problems with .mkv or avi files in all players.  it would be very pixelated and choppy.  but glxgears would show 2000+ frames per second!

Upon upgrading it warned me that fgrlx would no longer be supported.  I checked my xorg.conf file now after the upgrade and it is usig driver "ati" for video.

What's the difference between ATI and FGRLX? :)

---

### Post by Mortus Pryde on 2009-04-23
Okay, still newbie so won't be able to give you detailed answers, but savy enough to have learned whats going on. ;) I am sure some one will correct me if I go wrong, and thats fine. :)

9.04 no longer supports the 9.3 fglrx driver. So it reverted you to the open source ATI driver (Much like Windows would revert a system to a generic driver if it could not find a compatable driver laying around.).

Now the differance is from what I have been able to grasp, the fglrx has all the ATI/Radeon specs loaded into it and the most compatable support "Out-of-the-box". The ATI/Radeon drivers are open source and work fine for most basic 2D stuff but have limit or no video or 3D performance "Out-of-the-box" and may need xorg.conf tweaking.

That beind said! Check if your card is supported by the Catalyst 9.4, if it is you are golden, go ahead and install the new driver and you are off. If you are like me and running it on an older system then you may have to do the xorg.conf tweaking to get some if not all of the performance gains you had.

And that is the newbie to newbie guide while you wait for a more experianced member to fill in the blanks. ;)

---

### Post by usererror on 2009-04-23
I think that does help out!  I am not sure what catalyst my card supports.  But if it supports what you mention do I need to install the "official" driver from ATI then?  I had considered trying that before I upgraded to 9.04 just to see if it would fix the video jitters, but the upgrade has satisfied me for now.

---

### Post by Mortus Pryde on 2009-04-23
Before installing either of the fglrx drivers you really should ensure your card is supported or you may find your system will freeze and show a lot of pretty colors but be totally useless otherwise. ;) Been thought it many times myself, fixing it requires either going into commandline or reinstalling fresh. Personally since I have no data on my hard drive I just reinstall and chalk one to experiance. ;)

---

### Post by usererror on 2009-04-23
Looks like my card has gone Legacy now.  ATI will only let me download 9.3 of the Catalyst software.  My card is a Radeon X800SE

---

### Post by alphacrucis2 on 2009-04-23
> **usererror said:**
> Looks like my card has gone Legacy now.  ATI will only let me download 9.3 of the Catalyst software.  My card is a Radeon X800SE

That sucks. You need the 9.4 Catalyst to be compatible with Jaunty's x server 1.6. It means you have to use one of the open source drivers. I'm told that when ATI legacied the cards that dropped out of 9.4 they released the full docs for those cards, so the open source devs should eventually be able to get all the bells and whistles of those cards going in the open drivers.

---

