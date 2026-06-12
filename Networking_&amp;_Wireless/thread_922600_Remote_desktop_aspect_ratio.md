---
title: "Remote desktop aspect ratio"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by wtfbrb on 2008-09-17
I have a wide screen laptop and a 4:3 desktop.  Windows remote desktop handles this no problem, why can't I get it to work on ubuntu/vnc?  Is there anyway I vnc into my ubuntu machine and have it display correctly in widescreen format?

---

### Post by yogensha on 2008-09-18
That's a tough one.  Remote desktop handles this by actually creating a new desktop that's the same size as the client machine.  This can sometimes have the somewhat annoying effect of rearranging the icons on the target machine, and is also why you can't interact with the system locally while somebody is using RDC.

VNC works much differently.  It actually reproduces the screen of the target machine on the client, including the resolution and aspect ratio.  The advantage is that the local and remote user(s) can all interact with the machine simultaneously.

Some modern VNC clients have a scaling option.  I use this all the time for making my high resolution desktop display fit on my much smaller laptop display without having to scroll around.  I haven't seen any clients that will scale horizontal and vertical separately.  That would change the aspect ratio, but might distort the display such that it's not usable.

That's the long answer.  The short answer is, unfortunately, no.  You may be able to work with it with the scaling options on some of the modern clients though.

---

