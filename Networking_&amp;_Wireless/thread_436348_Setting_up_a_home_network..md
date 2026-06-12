---
title: "Setting up a home network."
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Madmoose on 2007-05-07
Hello, 

 I have been looking all over, but I can't seem to find the HOWTO to my problem. I have two Ubuntu 6.10 desktops at my home. There are windows computers, but I'm not interested in networking with them. I just want these two linux computers talk to each other. 

I know how to set up a home network for file sharing, printer sharing, and ect on windows. It's easy... Very easy. Yet, I can't find out how to do it on Ubuntu. Someone told me it was easier to hook two linux computers together, but I can't seem to figure it out. 

I've installed the System-Admin-Shared Folder with Unix support, and I've set it up so the other computer's hostname can see said folder. Even when I set it so both computers can see folders, and both hostnames are in the fields I can't get them to see each other. 

Maybe I'm trying to find them wrong. To find the computers I'm going to Places- Network servers- nothing...

Does anyone know how to set up this up, and or know where to find the HOWTO to get this to work. I don't think it should be this hard... really.

Thanks, 

Moose.

---

### Post by dmizer on 2007-05-07
if you do not want to have windows machines talk to your ubuntu computers, use nfs.  all the tweaking you've done to this point to try to get your shares to work has been with samba, a windows networking protocol.

have a look at the 4th link in my sig for your howto.

---

