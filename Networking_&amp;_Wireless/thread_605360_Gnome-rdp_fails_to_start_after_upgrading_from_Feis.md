---
title: "Gnome-rdp fails to start after upgrading from Feisty to Gutsy"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by R00t3rMan on 2007-11-06
Hello all!

I'd been running Feisty on my laptop for several months now and I decided to upgrade to the latest and greatest (Gutsy 7.10)...as they say, if you want to be on the bleeding edge, be prepared to bleed.

Since my kernel upgrade, I cannot get gnome-rdp to start (worked fine with Feisty).  I get the following message on a pop-up window:

Error in query:
SELECT * FROM version WHERE id = 1
Error:file is encrypted or is not a database

**OK**

There was an error during reading of record.

**OK**

Invalid database version!

**Close**


***scratches his head and tries sudo apt-get install gnome****  ((What the hell?)

NOPE


I'm running Gnome 2.20.0, 


Are there any logs I can check to see what's happening?  I don't mind doing the work just so long as I have microbrew and nicotine.  Quick fixes are always nice, but I'm having a blast "looking under the hood," and this isn't by any means an emergency.  Please, tantalize me with clues.

Let me know if there is any additional information you need to assist and keep in mind that I'm just a router guy with rudimentary computer skills.  I'm fearless in the cli (maybe that's my problem), but I may ask some seemingly dumb follow-up questions.  Also, if anyone feels I should have posted this in the newbie section (or on ubuntuforidiots.com/rtfm) just tell me; it won't hurt my feelings.

---

### Post by Endolith on 2007-11-07
I have this problem too.  I've tried complete uninstall, purge, dpkg reconfigure.  Nothing works.  I've been using Terminal Server Client instead.

---

### Post by R00t3rMan on 2007-11-08
That was too easy.  Many thanks for sharing your workaround!!

---

### Post by Endolith on 2007-11-08
> **R00t3rMan said:**
> That was too easy.  Many thanks for sharing your workaround!!

That's not a workaround; it's an alternative.  :-)

It seems like Gnome-RDP is more "integrated into the desktop", so it seems like it would be preferable, since I use VNC and RDP every day.  But it won't work and I have no idea why.

---

### Post by mitchc2 on 2007-11-19
I just started having this problem even though I upgraded to Gutsy a few weeks ago.  Anyway, it looks like somehow sqlite 2 was removed from my system during an upgrade, and replaced with sqlite3, which isn't reverse-compatible it seems.  I fixed the problem by installing libsqlite 2.8.17-2.  They can both be installed at the same time so I suspect that's all there is to it.

HTH!

Colin

---

### Post by Endolith on 2007-11-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/163951](https://bugs.launchpad.net/ubuntu/+bug/163951) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				That fixed it for me too!  Package is libsqlite0.

---

### Post by Endolith on 2007-11-19
AHA!  It was opening, but the actual connection still wasn't working, so I kept searching and found this:

[http://ubuntuforums.org/showthread.php?t=523103](http://ubuntuforums.org/showthread.php?t=523103)

This gets the same fix without libsqlite0 installed, just by deleting the configuration file.  So it seems the actual problem is that the configuration file needs to be updated to the latest database version, instead of installing the older version of the library.

The connection still doesn't work, though.  It pops up a dialog telling me the options for tightVNC and doesn't do anything else:

> TightVNC viewer version 1.2.9

Usage: /usr/bin/xtightvncviewer [<OPTIONS>] [<HOST>][:<DISPLAY#>]
       /usr/bin/xtightvncviewer [<OPTIONS>] [<HOST>][::<PORT#>]
       /usr/bin/xtightvncviewer [<OPTIONS>] -listen [<DISPLAY#>]
       /usr/bin/xtightvncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME>
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor

Option names may be abbreviated, e.g. -bgr instead of -bgr233.
See the manual page for more information.

---

### Post by Endolith on 2007-11-19
> **Endolith said:**
> The connection still doesn't work, though.  It pops up a dialog telling me the options for tightVNC and doesn't do anything else:

And that appears to be caused by a bug when you click "save password":

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg143017.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg143017.html)

fixed in 0.2.2-3?

---

### Post by starbugx on 2008-04-25
Here is a way to read the old .gnome-rdp.db and a workaround to start without errors:

[http://ubuntuforums.org/showthread.php?p=4790024](http://ubuntuforums.org/showthread.php?p=4790024)

---

