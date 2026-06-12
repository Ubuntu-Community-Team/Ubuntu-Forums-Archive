---
title: "ushare &amp; ics"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by doitforchuck on 2008-05-03
Ok, here's the problem:
I've got my xbox360 running on a wired connection to my ubuntu box, which in turn connects over wireless. It works fine; I can connect to xboxlive, no problems.
I tried installing and running ushare. It worked at first and I could see the share on the xbox360. After a restart of both the xbox360 and my box, I can no longer see the share on the xbox360.
I'm pretty adamant about using ushare and not anything else, because I've [I]seen[I] it work before. Anyone have any experience with this? Perhaps there's something wrong with my ics?

---

### Post by itix on 2008-05-03
I don't have uShare but I'll assume that it works like my mediaTomb media server that I use for my PS3 and my Asus Eee, ie sharing media through UPnP. Did you hardkill = shut ushare with the machine? I had serious problems with my mediatomb when I hard killed it, because the database became corrupt. That may be your case. Do you have a .ushare folder in your home directory?
You can see hidden files with *ctrl + H*.

---

### Post by doitforchuck on 2008-05-03
I don't seem to have a .ushare in my home.

On a side note, I still can access the web interface

---

### Post by itix on 2008-05-03
Hmmm. I could also acess the web UI while the server db was corrupt. How do you start the server? Mine is started through the terminal, and they seam quite alike.

---

### Post by doitforchuck on 2008-05-03
I start it with "ushare -t -w -x -f /etc/ushare.conf"

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 10.0.0.1:49593
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/disk/movies
Looking for files in content directory : /media/disk/tv
Found 332 files and subdirectories.

Otherwise with just "ushare -x -c /etc/ushare.conf" I get the "bind: Address already in use" error

---

### Post by cub on 2008-05-04
Everytime I start my computer ushare is already running, but I can't connect to it from my xbox360. I need to kill the running ushare and then start it manually with "ushare -x" and then everything works again. Tiresome to have to do this everytime I reboot but it's working.

---

### Post by itix on 2008-05-04
I don't know if this is a general linux command but before you reboot the next time, try going to the terminal that is running your uShare and pressing ctrl + c. That shuts my server down befor I shut my computer down.

If ushare automatically added an entry to system => preferences => session, try removing that and start the server manually. 

I entered an entry there manually but that's what caused the corruption since I couldn't shut the server down with *ctrl + c*. Try cubs post and then starting it up again and see if you can shut it down with *ctrl + c*

---

