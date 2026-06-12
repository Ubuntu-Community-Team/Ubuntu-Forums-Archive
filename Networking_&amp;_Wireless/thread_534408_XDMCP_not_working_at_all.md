---
title: "XDMCP not working at all"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by campioni on 2007-08-25
Hello, I've tried to login to Ubuntu remotely from a Windows XP machine without any success. I'm using Xming and enabled XDMCP on my Ubuntu machine, but all I get is a blank window, no login screen or anything.

Tcpdump gives me the following upon starting the request from the XP machine:
```
192.168.0.6.1048 > 192.168.0.7.xdmcp: UDP, length 7
```

But that's all. Been looking around the web for days trying to find a solution with no luck at all!

Any help would be greatly appreciated.

---

### Post by jonmartin on 2007-09-13
Yup, same prob trying to log on from another Xorg machine (SuSE 10.2). I get no login screen, but the kubuntu machine (7.04) is displayed in the SuSE remote login selector so it's at least broadcasting. It also seems another xserver is trying to fire up on the kubuntu box, because i need to use Ctrl.Alt.F7 to get back the session I had. On the SuSE-box all I see is a black screen with the X-cursor in the middle. No logon screen.

I think it's pretty lame that xdmcp isn't even supported in the kubuntu system setup tool. On SuSE and RedHat/Fedora it's just a matter of ticking of inn the setup tool and it just works.

I've edited kdmrc and Xaccess on my kubuntu to enable xdmcp. Is there anything else that need to be done? I've seen a ton of postings regarding xdmcp but no solution. However, for some it seem to work flawlessly, though ...

---

