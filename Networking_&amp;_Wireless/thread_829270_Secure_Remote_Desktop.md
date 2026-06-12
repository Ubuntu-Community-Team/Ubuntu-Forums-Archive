---
title: "Secure Remote Desktop"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by ubtBaba on 2008-06-14
My issue is when I connect to my linux box everything I do is visible; after I login remotely my linux box is open to whomever is in my room at the moment.

When I used Remote Desktop on my Windows machine the screen would lock and that gave me some sense of security and saftey.

Can I do something about this security issue?

---

### Post by LordSarpedon on 2008-06-18
This is a missing feature that I've yet to find a workaround for. Both Windows and Mac OS have had this capability for ages.

Perhaps this should go on a bugtracker somewhere? Point me.

I tried to explain this use case on an IRC channel recently - many don't seem to get it. So a recap.
On Windows, a *very* common pattern in the workplace is to lock the screen (or let it go to screensaver), go home, and log in with remote desktop. Doing so connects to the existing session. You can just pick up where you left off. The local display remains locked - you cannot see if anyone is connected or what they happen to be doing. If the user is not already logged in, a new session can be created. The local screen will indicate "locked." Even though the session was started via remote desktop, a local user can still log in. Logging in locally disconnects remote users. Logging in remotely locks the screen. Makes sense.

On Linux, NX is fantastic for remote access. Much faster than Remote Desktop, in my experience. But an NX session cannot transition to the local display and input devices.

VNC can be handy, but it also doesn't solve the problem.
Using a special VNC X server, one can have resumable sessions, but these sessions are once again independent of the local display and cannot transition to / from the "real" X server.
Another use case involves either a VNC extension or process that attaches to the real X server.

So then, the primary method of connecting to the local display seems to be through the polling versions of VNC. It works for what it is basically supposed to do - for "Desktop sharing" purposes it makes sense. The issue in this means of control of a "real" X server is that everything still gets drawn on the screen, the mouse can be seen moving, local input devices still work, etc. In the workplace example, anyone can sit there and watch what you do as you do it. Or do something dangerous with your privileges. Not only is there _no giant flashing warning_ about this when using 'desktop sharing', it lacks a lot of utility that the Windows and Mac equivalents have.



Vague implementation proposals (Translation: I'm a Windows developer that knows just enough about Linux to get this wrong)

1. A second X server (Probably easiest, maybe even possible)
Look at how the 'Switch User' function of the modern display managers seem to handle things. Switching users locks the screen but then switches to a newly spawned X server. A new user can then log in. Switching VTs manually simply reveals a 'locked' screen, same as the prettier method of using 'Switch User' again. More or less a creative use of existing VT isolation / functionality.
I'm going to test this shortly, but I believe VNC still polls normally even if the X server doesn't have the active VT.
Some additional considerations - For user switching, VTs are not a security boundary. Switching to a logged in session requires one to unlock. In this little hack, I suppose one would have to disable local VT switching (just to the vulnerable VNC one possibly?) or detect the switch and immediately lock.


2. Imaginary Screen (Messy, probably difficult)
Special, imaginary "VNC" screen configured for X. Doesn't correspond to an actual screen (possible without patching...?). When a VNC client connects, the actual desktop and imaginary 'screen' are swapped. The local display shows a "Locked" dialog. The invisible display is not drawn to a monitor as it was previously, but the VNC extension/process can still poll it for updates.
Additional Considerations - input devices. Mouse, keyboard focus needs to be handled a bit differently. Both screens need to have a pointer and need to be able to type, but each pointer should be trapped to one screen. Perhaps the existing 'Multi-pointer X' patches could help here. Perhaps less bugs to worry about as the two pointers could never be near the same app.


Experts, please correct me as needed.

---

