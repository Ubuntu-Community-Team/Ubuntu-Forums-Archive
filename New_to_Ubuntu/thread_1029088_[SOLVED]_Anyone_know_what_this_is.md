---
title: "[SOLVED] Anyone know what this is?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by tropdoug on 2009-01-03
I visited a site for learning ESL and this window (below) popped up, I closed it, moved on in the site and up it came again I am very wary of this as it seems like a possible attempt to gain access to my machine, maybe similar to a 'trojan' in windows. Does anyone know what it is, or whether it is malicious or not.

---

### Post by efexD on 2009-01-03
A .xcf is a format used by GIMP. In other words its just a picture.
Yet again, i'm not 100% positive that it IS that. But a .xcf is a format used by GIMP.

---

### Post by psycosmyth on 2009-01-03
Were you chatting on an IRC channel?
I have seen this before when chatting, just odd info like an image as efeXor stated.

---

### Post by tropdoug on 2009-01-03
Thanks Guys, I think my explanation was not so good. The image is a screen capture of the dialog box that pops up. I saved it as an xcf file which your correct is the default file format in Gimp. 

Of course I now realise that if your not using Gimp you wouldn't see the file -- I am not on my own puter right now, so I will repost it tomoorw as a jpg. But hey thanks for the try, my fault for not thinking.

---

### Post by txcrackers on 2009-01-03
Okay, the dialog you're getting is for a JNLP (aka "WebStart") Java program. The program (Netx) apparently needs caching space. The Netx program/JNLP should have prompted you before this to allow or disallow access to your local system **and** signed by a security certificate.

If you don't trust the program to run and access your local machine, you won't be able to use your e-learning site. JNLP programs usually run in a security sandbox and can't do anything to your system without you knowing about it (generally). Plus, trojans are damned hard to do on Linux/Unix systems if you're *not* the root user (which is typically not the case on Ubuntu).

The decision is basically up to you: do you trust this site or not?

---

### Post by tropdoug on 2009-01-03
Cool. txcrackers, thanks for that. Yeah the site seems to be genuine, I just had never seen this sort of pop up since I have been using Linux, (about a yr now) so I just wanted to be sure. 

Thanks for the help

---

