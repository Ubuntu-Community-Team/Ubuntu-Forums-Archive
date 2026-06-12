---
title: "Firefox can't run new window in second X Screen...?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by pablolie on 2009-11-25
I have a dual monitor configuration, running them as separate X Screens.

I can open as many Firefox windows as I please within the same X Screen aka monitor. However upon trying to start Firefox from the second one it'll complain that a Firefox instance is already running and shut down (Firefox). 

I assume it's a configuration issue with the nvidia-settings, but not sure what to look at. Any ideas pointers? It is quite limiting to not be able to run a second instance of an application on the second monitor...

---

### Post by EndPerform on 2009-11-25
The reason for this is that it's treating the second monitor as a separate X session.  When you start Firefox a second time in the same X session, it realizes that there is an instance in that same session running.  However, if you start it from a different session, it only sees that the Firefox binary is out there but doesn't see Firefox on this particular X session.  

I have the same problem when I'm working remotely and I start a FreeNX session.  I have to kill the running Firefox, which is on a different X display.  

Best bet would be to have the second monitor extend your first desktop and eliminate the multiple X sessions.

---

### Post by pablolie on 2009-11-25
> **EndPerform said:**
> The reason for this is that it's treating the second monitor as a separate X session.  When you start Firefox a second time in the same X session, it realizes that there is an instance in that same session running.  However, if you start it from a different session, it only sees that the Firefox binary is out there but doesn't see Firefox on this particular X session.  

I have the same problem when I'm working remotely and I start a FreeNX session.  I have to kill the running Firefox, which is on a different X display.  

Best bet would be to have the second monitor extend your first desktop and eliminate the multiple X sessions.

Thanks.

So basically just work with Twinview as opposed to separate X Screens?

---

### Post by EndPerform on 2009-11-25
> **pablolie said:**
> Thanks.

So basically just work with Twinview as opposed to separate X Screens?

Yep, that should take care of it and give you what you're looking for.

---

### Post by Nick Payne on 2009-11-28
I have the same problem, but as my 2nd monitor is rotated I think I am stuck with using separate X screens. I wasn't able to get the rotation to happen on the 2nd monitor when using Twinview. I like to run Firefox on screen 2 and my e-mail client on screen 1, but this means that I can't click on a link in an e-mail or I just get the same error as the OP reported of a dialog saying "Firefox is already running but is not responding".

Is it possible to rotate the 2nd monitor using Twinview?

---

### Post by DirkH_ on 2012-01-06
Hello, 

I just found out while investigating the same issue: firefox in screen 2, mail in screen 1, "already running" error, etc. Just try this:

- open terminal
- type: 

export DISPLAY=:0.1 (screen where firefox runs, mail client runs in :0.0)
xdg-open "http://www.google.com"
firefox "http://www.yahoo.com"

Both of them work as expected! You can try to solve your issue by writing a wrapper script or something similar for the default url handler...

Cheers!
Dirk

> **Nick Payne said:**
> I have the same problem, but as my 2nd monitor is rotated I think I am stuck with using separate X screens. I wasn't able to get the rotation to happen on the 2nd monitor when using Twinview. I like to run Firefox on screen 2 and my e-mail client on screen 1, but this means that I can't click on a link in an e-mail or I just get the same error as the OP reported of a dialog saying "Firefox is already running but is not responding".

Is it possible to rotate the 2nd monitor using Twinview?

---

