---
title: "Opening a port"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by japhyr on 2010-11-04
Hello,

I am trying to use eboard to connect to a chess server, and I think it is a port-related issue.  The eboard interface seems to use port 5000.

If I run```
telnet freechess.org
```I connect to the chess server.
If I run```
telnet freechess.org 23
``` I am also able to connect.
But if I run```
telnet freechess.org 5000
``` I am unable to connnect.

How can I open port 5000, at least for this program?

---

### Post by bioterror on 2010-11-04
By default the outgoing traffic is not closed, but incoming is in firewalls.

It can be possible that your internet service provider has blocked some ports if it's not working.

---

### Post by sikander3786 on 2010-11-04
Or it might also be your router blocking that port.

As mentioned, outgoing traffic is not blocked in firewalls. Even ufw is not enabled by default on Ubuntu unless you yourself enabled it. You can check the status by

```
sudo ufw status
```

If you need a GUI for ufw, you can use GUFW.

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by japhyr on 2010-11-04
```
sudo ufw status
```shows disabled, so I don't think that is the issue.

I tried port forwarding on port 5000, but that did not seem to solve the issue.

Any hints where to look next?

---

### Post by NertSkull on 2010-11-04
You can check your router to make sure its not blocking anything.

Also maybe try an third party site(at your own risk) to see if the port is open at all.

For example [www.canyouseeme.org](www.canyouseeme.org) is one I use from time to time to see what's open.

If they can't see you, and you are SURE everything is open on your end.  Maybe contact your ISP and ask if they block things.

---

### Post by CharlesA on 2010-11-04
If you are able to connect on port 23, why not use that port?

---

### Post by japhyr on 2010-11-04
> **CharlesA said:**
> If you are able to connect on port 23, why not use that port?

I'm not sure how to change the port that eboard uses.  I looked in all the menus, and looked at the configuration files as well.  It seems like something that would be easy to change, but I can't figure out where the port # is specified.

---

### Post by CharlesA on 2010-11-04
If you run eboard, does it connect, or no?

See here: [http://www.freechess.org/Help/QuickGuide/index.html](http://www.freechess.org/Help/QuickGuide/index.html)

---

### Post by japhyr on 2010-11-04
I have not been able to get eboard to connect.  I get an error "Connection to freechess.org:5000 failed: Unknown error".  This is why I think it's a port issue.  I am pretty sure if I could get eboard to use port 23, it would work.

---

### Post by CharlesA on 2010-11-04
I've not used it, but if the chess server is running on port 23 instead of 5000, there should be some way to tell it to connect to a specific port.

---

### Post by japhyr on 2010-11-11
I ended up digging through the source code, and found that using port 5000 was hard coded in two places.  I changed those two places to 23, compiled, and it works.  In the process I learned a bit about using patches, which was a very valuable experience.  Thank you everyone.

---

