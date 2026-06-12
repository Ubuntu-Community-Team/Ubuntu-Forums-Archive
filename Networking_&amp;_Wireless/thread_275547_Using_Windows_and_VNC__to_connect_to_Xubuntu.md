---
title: "Using Windows and VNC  to connect to Xubuntu"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by cocotu on 2006-10-11
Here at work I intalled VNC on my Win machine and also on my Xubuntu machine. I'm able to connect using vnc from Xubuntu to windows, but NOT able to do the same from Windows to Xubuntu.

When I type [COLOR="Blue"]vncserver[/COLOR] at my Xubuntu machine I get:

> New 'X' desktop is XubuntuLab:3

Starting applications specified in /home/xrgm/.vnc/startup
Log file is /home/xrgm/.vnc/XubuntuLab:3.log

When I go to my Windows machine and run the viewer and type the Xubuntu's IP I get:

> Unable to connect to host: Connection refused(10061)

When I type the Xubuntu's host name I get:

> Unable to resolve host by name: No more results can be returned by WSALookupServiceNext. (10110)

What should I do to resolve this? Is there something else I can use to connect using GUI from Win to Xubuntu and vice-versa.
Thanks....

---

### Post by mitch.c on 2006-10-11
> **cocotu said:**
> When I go to my Windows machine and run the viewer and type the Xubuntu's IP I get:

When I type the Xubuntu's host name I get:

What should I do to resolve this? Is there something else I can use to connect using GUI from Win to Xubuntu and vice-versa.
Thanks....
Based on your post (which isn't quoting properly), you need to connect on display 3. So when you run vncviewer, try ip_addr:3.

Host name doesn't work because without a dns entry, or host record on the windows machine, window can't resolve the hostname.

---

### Post by cocotu on 2006-10-12
I still get the same error!

---

### Post by Face1 on 2006-10-14
I'm having the same issue!  If anyone resolves this please post the solution.

---

### Post by Moriak on 2006-11-30
> **mitch.c said:**
> Based on your post (which isn't quoting properly), you need to connect on display 3. So when you run vncviewer, try ip_addr:3.

Host name doesn't work because without a dns entry, or host record on the windows machine, window can't resolve the hostname.

Worked fine for me. Are you sure you type everything correctly?
Try to ping first, maybe you don't even have a route to your xubuntu host??

in console:
```

ping xubuntu_ip_add

```

---

### Post by alex_noobuntu on 2006-12-13
> **Moriak said:**
> Worked fine for me. Are you sure you type everything correctly?
Try to ping first, maybe you don't even have a route to your xubuntu host??

in console:
```

ping xubuntu_ip_add

```

I have same issue:
I can ping from windows xp box
Started VNC via:
  labguy@halibut:~$ vncserver

  New 'halibut:1 (labguy)' desktop is halibut:1

  Starting applications specified in /home/labguy/.vnc/xstartup
  Log file is /home/labguy/.vnc/halibut:1.log

  labguy@halibut:~$ 

ps ax shows:
  7810 pts/4    S      0:00 /bin/sh /home/labguy/.vnc/xstartup
but this process quits after a few seconds and I am unable to connect to vnc

logfile shows:
[email]labguy@halibut:~/.vnc[/email]$ cat halibut\:1.log 

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Dec 13 15:04:23 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/misc/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'halibut:1'
/home/labguy/.vnc/xstartup: 12: twm: not found
vncconfig: unable to open display "halibut:1"
xterm Xt error: Can't open display: halibut:1
[email]labguy@halibut:~/.vnc[/email]$ 

So I try to install twm via dselect and last few lines of log are now:
Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'halibut:1'
vncconfig: unable to open display "halibut:1"
xterm Xt error: Can't open display: halibut:1
twm:  unable to open display "halibut:1"



Can anyone help from here?

---

### Post by terry_opie on 2006-12-28
I'm also seeing this same symptom.

I'm not new to Linux, but this is my first install of Ubuntu...  Seems odd that there are so many hoops to run through to try to get VNC working.  I read through the "install" threads for Xvnc, none of the suggestions made worked.  I've never had this kind of problem on other distros.  (mainly RedHat)

Back to the problem, I can ping the Ubuntu box, even connect via Putty to get a prompt, but vncserver when started only stays running for a few seconds, then quits.  But the pid file persists in the .vnc directory.  Which I take as meaning that the process was still trying to run?!?  Not sure.  I'm seeing the same messages in the log files within the .vnc directory...   

Any ideas??

I'm trying to get familiar with Ubuntu to help switch to Ubuntu for some work related items, but if this is such a problem, we'll probably scratch the idea and stick with Red Hat...

---

### Post by uberground on 2007-01-08
vncserver -fp /usr/share/fonts/X11/misc
Fonts are not where they're expected to be.

See *[Xubuntu Remote Desktop with VNC4Server]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html")* for walkthrough

---

### Post by muzzamo on 2007-04-20
What is the best way to add this to xubuntu startup?

Thanks

---

