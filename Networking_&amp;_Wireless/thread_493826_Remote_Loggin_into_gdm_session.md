---
title: "Remote Loggin into gdm session"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by NeoParabola on 2007-07-06
Hi all, 

I'm trying to set a remote pc to loggin from anywhere to my computer via a ssh encrypted tunnel whit putty. Actually, the tunnel il working fine when done whit putty and then I use VNC viewer to have visual support. I then wanted to go a step further by setting a wakeonlan magic packet based startup wich is working too. The last step i have to do is to make vncserver be active enven before i'm logged so I can handle loggin from my remote computer. I know this can be done using XDMCP but I would like to hear wathever you can tell me to proceed! Thx!

---

### Post by horstkotte on 2008-01-14
Hi NeoParabola, 

I am about to set up the same infrastructure to be able to access my Ubuntu system remote from work and was wondering if you still have more detailed instructions on how you succeeded and if there were any pitfalls. 
Especially the performance of VNC would interest me. I heard it is kinda sluggish. I was rather thinking of either only exporting the x session or using a remote GDM. 

Did you get the wake-on-lan running? This would be a great benefit for me as well.

Thanks!!

---

### Post by ziemniak on 2008-01-18
in gdmsetup you can configure xdmpc

---

