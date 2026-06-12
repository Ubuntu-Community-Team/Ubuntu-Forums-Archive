---
title: "resume physical session - a remote desktop solution wanted"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by fermulator on 2008-10-05
Good afternoon fellow Ubuntu'ers!

I've recently switched from Windows and moved to Ubuntu and I'm looking to find a way to match the functionality of certain "window isms".  In particular for this post, remote desktop.

**_Windows Scenario #1:_**
[LIST=1]
[*]Log into Windows, do stuff ... open some things ...lock screen
[*]Leave physical location (i.e. go to work)
[*]At work the next day, using RDP (appropriate ports forwarded on router of course), I can remote desktop into my Windows box and resume the physical console session I was using the previous day, with all my applications in the same state, etc.
[/LIST]

**_Windows Scenario #2:_**
[LIST=1]
[*]Boot windows ... the Windows logon is displayed ... we don't login
[*]Leave physical location (i.e. go to work)
[*]At work the next day, using RDP (appropriate ports forwarded on router of course), I can remote desktop into my Windows box.  Do stuff .. open things .. etc.
[*]Closing the remote connection, go home
[*]Physically at the PC again, I can login, and resume the 'virtual session' that was created earlier that day.
[/LIST]

How can we accomplish these same type of use cases in linux, and in particular of course, for Ubuntu?

I'm aware of several remote desktop methods including X11 VNC using SSH tunelling, and no machine's NX client/server.  I'm not sure however how to 'hook' these remote connection sessions into the physical login of ubuntu. i.e.:

**_Ubuntu Scenario #1_**
[LIST=1]
[*]Login to Ubuntu (physically) ... gnome loads.  Do stuff ... use the system.  Lock the screen.
[*]Go somewhere else ... (i.e. to work)
[*][COLOR="DarkRed"]**QUESTION**: how to remotely connect to my Ubuntu box and resume that physical session?[/COLOR] - POSSIBLE SOLUTION: VINO - [http://ubuntuforums.org/showthread.php?t=472998](http://ubuntuforums.org/showthread.php?t=472998)
[/LIST]

**_Ubuntu Scenario #2_**
[LIST=1]
[*]Boot Ubuntu, but don't physically login to GNOME (i.e. a WOL scenario)
[*]Go somewhere else ... (i.e. to work)
[*][COLOR="DarkRed"]**QUESTION**: how to remotely connect to my Ubuntu box without already being logged in?[/COLOR]
[/LIST]

I suppose ultimately I need that hybrid of scenario #1 and scenario #2.  Is this possible?  I know now that we can use "VINO" for scenario #1, and, say, NX Client from 'nomachine' for Scenario #2 ... but it would be beneficial to have the *same solution* for both problems...

The community's expertise is greatly appreciated!

Thanks,

---

### Post by alberto ferreira on 2008-10-05
Here it is:
[http://ubuntuforums.org/showthread.php?t=472998](http://ubuntuforums.org/showthread.php?t=472998)

---

### Post by fermulator on 2008-10-06
> **alberto ferreira said:**
> Here it is:
[http://ubuntuforums.org/showthread.php?t=472998](http://ubuntuforums.org/showthread.php?t=472998)

Oh thanks!  I'm sorry I wasn't detailed enough in my initial post, I've updated (edited) it.

Looks like VINO solves my first scenario, but I need also the second scenario, with the goal of using the same solution (software/method) for both.

---

### Post by veloce on 2008-10-07
> **fermulator said:**
> Good afternoon fellow Ubuntu'ers!


**_Windows Scenario #1:_**

**_Windows Scenario #2:_**


**_Ubuntu Scenario #1_**

**_Ubuntu Scenario #2_**

Thanks,

Windows Scenario's 1& 2 are handled by rdesktop which is a linux implementation of the rdp. gnome-rdp is a nice front end to this.  The only trouble you may run into is picking up a running session - this should work fine for a single user version of windows but will not for windows server without some fettling. (This may involve using rdesktop from the command line to get the right session.)

Ubuntu scenarios.  XDMCP is the best tool for this but I'm not sure about picking up an existing session.  As linux is naturally multi-user it will act similar to windows server. Again, it's probably possible but may take some fettling to get right.

Fundamentally, the windows "functionality" you are looking for relies on some limitations of windows compared to linux. That is, windows is fundamentally single user so there is only one session per user; linux allows many sessions per user.

---

