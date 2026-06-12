---
title: "Remote Desktop (Secure)"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by 141N on 2007-09-19
Hey all, sorry for posting such a tedious and n00b question but I'd like to know how to remotely connect to a computer securely. I have feisty and it has the built-in Remote Desktop tool, but I hear whispers that it is un-secured, so any data passing between two computers is easily picked up via packet-sniffers.

I heard that you can setup Remote Desktop through SSH to make it more secure but I haven't the faintest idea how to do that

can someone help me or point me to a good article?

-Iain-

---

### Post by kevdog on 2007-09-19
You can either use VNC tunneled through an SSH server or FreeNX which is also tunneled through an SSH server.

FreeNx is much faster than VNC, however is much more painful to setup.  It also gives you a separate desktop session, so that if you are on the client and another person is on the server, you get a separate session on the server -- you dont see the same desktop

VNC is the old standby -- both the client and server share the same desktop.

Both solutions require you have an ssh server/client up and running first.

---

