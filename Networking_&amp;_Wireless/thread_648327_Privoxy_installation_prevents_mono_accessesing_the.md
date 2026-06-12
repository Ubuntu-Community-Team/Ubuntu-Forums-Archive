---
title: "Privoxy installation prevents mono accessesing the Internet?"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by BroadArrow on 2007-12-23
I have an xmltv electronic programme guide grabber which runs on mono. It's been working fine until a couple of days ago when it started exiting with the following error:

> Failed to get latest configuration file: Error: ConnectFailure

The program author says that the grabber is failing to connect to the site where it needs to download the latest configuration file. It's also then failing to connect to any of the sites where it would download TV guide data.

The only thing I can think of that has changed in my system since the last successful guide update and the first unsuccessful one a couple of days ago is that I installed privoxy and TOR.

Is it possible that they could be interferring with mono's access to the Internet? 

I thought they shouldn't affect applications which don't use the proxy? I tried uninstalling them but that hasn't worked. Could the installation have interferred with settings somewhere that might affect mono?

Any help appreciated -- I'm desperate to have my guide grabber running before I go on holiday on Boxing Day so it can record programmes while I'm away!

Thanks in advance...

---

### Post by BroadArrow on 2007-12-25
Update: I've confirmed that the grabber works on a Windows machine on the same LAN so the problem looks like it might be that the privoxy and TOR installation are the cause.

Any ideas?

---

### Post by BroadArrow on 2008-01-02
Bump.

---

