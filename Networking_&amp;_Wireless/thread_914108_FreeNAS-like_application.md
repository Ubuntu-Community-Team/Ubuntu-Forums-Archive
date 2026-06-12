---
title: "FreeNAS-like application?"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by Apocrathia on 2008-09-08
I am in the process of re-purposing my old desktop to act as a NAS file server, amongst other random tasks. I ran across FreeNAS in a research frenzy and I am thoroughly impressed by its list of features... except that its a distro.
Is there any way to run FreeNAS as a service on an ubuntu-based machine. I am going to have the computer sitting in the closet with nothing more than power and ethernet hooked to it. all maintenance will be done via VNC. so I really like FreeNAS's web interface.
If I can't get freeNAS to run without the attatched distro, is there anything comparable. that will do AFP (netatalk) and has a full web interface?

If need be, I can just run it in a VMware machine in the background. It is an extremely light distribution. But I really want something that will run natively as a service. I already have SABnzbd+ on there plus a few other apps that have a webui, I'd really like to be able to manage my NAS from within my browser rather than have to open up a VNC connection. I know I am being pickly, but I just want things to work without much hassle.

---

### Post by MunkyJunky on 2008-09-08
If your only wanting it to run as a NAS, surely just installing the FreeNAS distro would work prefectly, and using admin via the web interface? 

If you want to have a few more features though, have a look into using Ubuntu server edition, I haven't checked, but I'm pretty sure there's  configuration for it to run as a file server avaliable at install. You can then install some VNC app to it (I've never used VNC, I'm not sure on how-to's for that) and manage it from your desktop. 

Otherwise, you could just use remote connection to the server without VNC and use terminal administration. I've never done anything like this myself though, so treat my words more as guidelines than a full solution! :)

---

### Post by Apocrathia on 2008-09-08
I have thought of trying ubuntu server edition, but isn't it a gui-less distro? To be quite honest, that scares the crap out of me for some reason.
I am running FreeNAS through Vmware on one of my PC's right now and I really REALLY like the usability of the webui. not having to worry with command line is nice.
Can't you simply install the majority of the server packages into the desktop version of ubuntu anyways? that's all I would probably end up doing.
Also, server doesn't support netatalk/afp, which is one of the main things i need as i own a few macs and primarily use OS X. I want to be able to setup shares for time machine, and for my appletv to use.
It's really starting to seem like I am going to have to run FreeNAS as a VirtualMachine in order to get the functionality out of it + a gnome environment in which to work on anything else.

---

