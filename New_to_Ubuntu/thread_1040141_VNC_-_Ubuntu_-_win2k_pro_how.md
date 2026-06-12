---
title: "VNC - Ubuntu - win2k pro how?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Bookmaster on 2009-01-15
Hi all,

I would like to have control over win2k pro machine from Ubuntu HH machine with VNC.
From another machine where I have winxp I can have control over win2k pro machine like this:

Open firefox, IPaddresswin2kpro:5800, and then I have to put my user name and pass and that's it.

How can I have control over win2pro machine from Ubuntu HH plaese?


Thanx

---

### Post by stevoo on 2009-01-15
i think 

sudo aptitude install vncviewer

may do the work. I am currently not home to see and let you 100% but i think this is what i used to use !

---

### Post by bloodniece on 2009-01-15
Well you could use VNC on the Win2k Pro machine.  TightVNC makes a mighty nice Windows x86 server.  It runs as a service and you can password protect it among other things.

_**[COLOR=Black]Windows[/COLOR]**_
Install TightVNC on the Windows machine.
[http://tightvnc.org/download.html](http://tightvnc.org/download.html)
Grab this one (latest):**[tightvnc-1.3.9-setup.exe]("http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9-setup.exe")**

Make a note of the machines IP or hostname


_**Linux**_
From the Linux box (assuming Ubuntu)
sudo aptitude install vncviewer
Alt+F2: vncviewer hostnameorwindowsmachine
or
Alt+F2:  vncviewer ipaddressofwindowsmachine

The technique/method you mentioned is using the Java applet from a web browser.  I've found that to be a little slow verus a normal VNC connection.  But TightVNC does offer a Java viewer. This also assumes the Windows box, if running a software firewall, has port 5900 open or whatever port you choose from the TightVNC setup/config opened.  If you use a non-standard port be sure to add that at the end of your vncviewer command. Example: vncviewer 192.168.0.50:5999

Cheers

---

### Post by Bookmaster on 2009-01-15
Just a stupid question:

If I already have installed VNC on win2k pro machine do I have to install tightVNC please?

Thanx

---

### Post by timcredible on 2009-01-15
why not use terminal services since it's already installed on xp by default and ubuntu has the client installed by default?  applications->internet->terminal server client

if you still want to use vnc, the client for it is also installed on ubuntu by default - applications->internet->remote desktop client

---

### Post by Bookmaster on 2009-01-15
> **timcredible said:**
> why not use terminal services since it's already installed on xp by default...


It is not XP it is win 2000 pro

---

### Post by Bookmaster on 2009-01-19
> **bloodniece said:**
> Well you could use VNC on the Win2k Pro machine.  TightVNC makes a mighty nice Windows x86 server.  It runs as a service and you can password protect it among other things.

_**[COLOR=Black]Windows[/COLOR]**_
Install TightVNC on the Windows machine.
[http://tightvnc.org/download.html](http://tightvnc.org/download.html)
Grab this one (latest):**[tightvnc-1.3.9-setup.exe]("http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9-setup.exe")**

Make a note of the machines IP or hostname


_**Linux**_
From the Linux box (assuming Ubuntu)
sudo aptitude install vncviewer
Alt+F2: vncviewer hostnameorwindowsmachine
or
Alt+F2:  vncviewer ipaddressofwindowsmachine

The technique/method you mentioned is using the Java applet from a web browser.  I've found that to be a little slow verus a normal VNC connection.  But TightVNC does offer a Java viewer. This also assumes the Windows box, if running a software firewall, has port 5900 open or whatever port you choose from the TightVNC setup/config opened.  If you use a non-standard port be sure to add that at the end of your vncviewer command. Example: vncviewer 192.168.0.50:5999

Cheers

I did everything as discrabed above and still cannot to connect from Ubuntu HH to win 2000 pro machine :(

In tightVNC on win 2000 pro machune I can see that I have to use 192.168.xxx.xxx:5901, so I put in Ubuntu HH machine ALT+F2 and than vncviewer 192.168.xxx.xxx:5901 and nothing is happening :(

Where am I wrong please?

SOLVED!

I should run Apps / Internet / Remote desktop viewer.


If any of amdnis read this msg put SOLVED on Subject.

Thanx

---

