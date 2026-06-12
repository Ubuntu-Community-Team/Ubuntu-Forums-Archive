---
title: "Remote Desktop Question"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Corinos on 2009-12-18
Hey all,  Trying to get a vnc remote connection working on my Kubuntu box.  So far I can have a brother connect, but I have to accept his request.  I want to be able to connect remotely myself, so I won't be here to accept my request.  Is there something I'm doing wrong?

Cor

---

### Post by pricetech on 2009-12-18
I don't use that any more, but it seems I recall that was one of the settings, whether to require confirmation or not.

---

### Post by t0p on 2009-12-18
I don't know about vnc.  To log in remotely, I use **freenx** or **ssh**.  These solutions will involve installing the freenx server or ssh server on the machine you wish to log into.  Software is in the repos.

---

### Post by cenzorrll on 2009-12-18
go to system>preferences>remote desktop and it gives you some options on your vnc server

edit: if you plan on accessing this machine from outside your network (i.e. at work) you need to forward ports 5800 and 5900 i believe.

---

### Post by pricetech on 2009-12-18
> **cenzorrll said:**
> go to system>preferences>remote desktop and it gives you some options on your vnc server

edit: if you plan on accessing this machine from outside your network (i.e. at work) you need to forward ports 5800 and 5900 i believe.

5900 for the client software and 5800 for browser based connections.

---

### Post by smo0th on 2009-12-18
You need to make sure your router/gateway allows the port you use for VNC or configure VNC server+client to run under an allowed port.

---

### Post by microtaint on 2009-12-18
Is there anyway you can remote desktop to windows xp remote desktop from ubuntu?

---

### Post by Corinos on 2009-12-18
Thanks for all the ideas!  My router is working with the ports forewarded, and if I'm sitting at the machine, I see the dialogue for the incoming connection that I need to accept.  I have checked the setting in the Desktop Sharing configuration gui, and the box to ask for confirmation is cleared, but it still asks.

If I use SSH, can I still make it run the kde desktop?  I understand that it logs in to a prompt, but can I make t run X?

Finally, FreeNX.  I assume it works just as well?  I basically want the same functionality as Microsofts Remote Desktop, and so far the Desktop Sharing stuff in Kubuntu seems more like Remote Assistance...

Thanks, 

Cor

---

### Post by pricetech on 2009-12-21
> **microtaint said:**
> Is there anyway you can remote desktop to windows xp remote desktop from ubuntu?

Terminal Server Client is what you're looking for.  Works better than Remote Desktop under winders.  I use it all the time.

---

### Post by nerdy_kid on 2009-12-21
start krfb either via terminal or KRunner (called desktop sharing under INternet in menu)

hit configure
check allow uninvited connections
uncheck ask before allowing uninvited connections

might have to autostart it though on session login idk

---

