---
title: "Remote CDE desktop displayed on local WS"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by briansrapier on 2008-01-03
Good morning! 

I am trying to consolidate my working environments. I am using Ubuntu 7.10 as my primary desktop, but also use an XP workstation and a SunRay for access to various things and to troubleshoot user issues.

I have the XP environment working the way I want using rdesktop and seamlessRDP. However, the Solaris (CDE) desktop is a bit of a pain. I've tried multiple methods to get it working. My best attempt thus far has been to take the following steps:
```

Ubuntu: ssh -L7100:localhost:7100 -Y user@sunhost 
Ubuntu: xset +fp tcp/localhost:7100
SunHost: xhost + ; xauth merge ./.Xauthority ; Xnest :1 -pn -query localhost -once

```

Xnest comes up and presents a login screen after about 20-30 seconds. Following login the Xnest window goes black and then dies after just a few seconds. In the terminal I see:

```

sunDynamicLoadExtension: Open failed RENDER
AUDIT: Thu Jan  3 11:38:24 2008: 5724 Xnest: client 2 rejected from IP ::ffff:127.0.0.1 port 52720
AUDIT: Thu Jan  3 11:38:31 2008: 5724 Xnest: client 2 rejected from IP ::ffff:127.0.0.1 port 52722
AUDIT: Thu Jan  3 11:38:38 2008: 5724 Xnest: client 2 rejected from IP ::ffff:127.0.0.1 port 52724

```

Can anyone provide me with some insight as to why it's doing this?

---

### Post by briansrapier on 2008-01-04
I figured it out:

From my local machine I created a script:
```

ssh -L7100:localhost:7100 -Y USER@REMOTEHOST 'source ~/.profile;~/bin/start_cde' &
sleep 1
xset +fp tcp/localhost:7100

```

Then on the remote machine:
```

xauth merge ~/.Xauthority 2> /dev/null
Xnest :1 -ac -pn -depth 24 -geometry 1280x1024 -query localhost -once 2> /dev/null

```

---

