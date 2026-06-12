---
title: "Ubuntu Remote Desktop does not work"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by itsols on 2010-06-22
Hi, I'm trying to access my Windows XP Prof. PC from my Ubuntu 10.04 laptop. I tried my Remote Desktop Viewer. This is what I do:

1. I Start the program
2. Enter the IP address (of my Windows box on local network) in the HOST textbox.
3. Click connect.

But in a flash, I see a message "ubuntu Connection to host x.x.x.x was closed."

Does anyone have a solution to this?

I really appreciate some tips on this. Thanks!

---

### Post by c9-3Rr0r on 2010-06-22
Make sure that your Firewall @ Windows box allow connection for Remote Desktop, if I remember correct the default port is 3389

---

### Post by itsols on 2010-06-22
Thank you for your feedback.

On my Windows box, my firewall's turned off. Instead I have on it Kaspersky Internet Security 2010.

To add to it, the Windows box is actually a dual boot system. It's got Ubuntu 8.4 as well. At least when it's on Windows I get some window that closes instantly when I try rdesktop. But if I boot that into Ubuntu, I can't even access it.

Am I missing something?

Thank you once again!

---

### Post by bubonic1347 on 2010-06-23
I know this doesn't help at all, but I'm having the exact same problem. It's my Mythtv backend and my frontend. Mythtv works great, however the remote desktop gives the exact same error message as the OP.

I don't think it's operator error.

---

### Post by MartyBuntu on 2010-06-23
I've always had those same problems with built in Remote Desktop, so I switched to **xtightvncviewer**. Works perfectly, it seems faster and it's in the repositories.

---

### Post by itsols on 2010-06-23
I should then try tightvnc. But the reason I did not do it is because

1. I learnt that it is Java based - so THOUGHT it would be slower
2. I read on the docs somewhere that rdesktop on Ubuntu 10.4 has the same kind of functionality.

Anyway, I think I should try it out.

---

