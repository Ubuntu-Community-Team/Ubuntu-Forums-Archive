---
title: "XSessions"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by phmcguin on 2008-01-15
I can remote to my home machine from work using Putty via SSH on port 22. But all I get is the command line. Which is fine but sometimes I'd like to be able to open an application on my local machine. 

I've searched on this and found talk of XSessions/XWindows and Screen. Can someone point me in the right direction of what I should do to use this?

---

### Post by chewearn on 2008-01-15
1. You can forward X thru SSH by using:
```
ssh -X <user>@<server>
```

Then, in the ssh terminal you can execute a GUI program, e.g. gedit, the gedit window will appear right in your remote machine.

Putty can also run with X11 forwarding.  This even works for remote Windows XP machine (with Cygwin) .

2. Using the trick above, I can forward entire desktop by vncviewer:
```
vncviewer <server>
```

You just need to enable Remote Desktop, though it would probably be dirt slow.

---

### Post by csat on 2008-01-15
This article [=>here<=](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html) can give you some ideas...

---

### Post by phmcguin on 2008-01-15
I just tried: 

```
ssh -X <user>@<server>
```

I got the error message back...

```
cannot open display
press enter or any key to continue
```

Any ideas on why I'm getting this and what's needed to make it work?

---

### Post by d4ljoyn on 2008-01-15
You have an X server running on your client? For example on Windows you want XMing or cygwin/X -- if your client is Linux make sure the X server is fired up.

---

### Post by phmcguin on 2008-01-15
make sure the X server is fired up...

How do I do that then? I can figure out the install I'm sure..I'm guessing it's just a sudo apt_get "Xserver thing" but then what? do I need to do anything with it? configure etc?

Thanks so much for the replies and help!

---

### Post by chewearn on 2008-01-15
> **phmcguin said:**
> make sure the X server is fired up...

How do I do that then? I can figure out the install I'm sure..I'm guessing it's just a sudo apt_get "Xserver thing" but then what? do I need to do anything with it? configure etc?

Thanks so much for the replies and help!

Are you connection from what to what?  I mean what as in OS wise.

---

### Post by phmcguin on 2008-01-22
Connecting from Windows XP to Ubuntu 7.10 (Gutsy)

---

### Post by chewearn on 2008-01-22
You need to install this on your WindowsXP:
[http://www.cygwin.com/](http://www.cygwin.com/)

Make sure to select X during installation (it's not selected by default).

---

