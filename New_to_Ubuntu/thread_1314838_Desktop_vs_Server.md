---
title: "Desktop vs Server"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by hankyknot on 2009-11-04
It seems like a question that should have an obvious answer doesn't it?

I am currently rebuilding my PC's and Server to run virtually. The idea being virtual servers are much easier to restore in the event of a disaster. I am using VirtualBox for my hypervisor. My virtual clients will be running Windows XP, Vista, 7 and Server 2003, 2008. 

My question is this, as the "server" functions will be taken care of by the Windows operating systems can I run the desktop versions of Ubuntu or should I use the server version?

I like the desktop because its gui out of the box, whereas last time I tried server it was command line to start with and took a bunch of research and friggin with to get to a point where I found it usable.

---

### Post by iansane on 2009-11-04
Wait I thought virtualbox was just PC emulation software and not a hypervisor. I've been looking at citrix xen server because a hypervisor doesn't run on top of a server OS so it gets better performance. 

I was under the impression that running virtualbox or virtualPC on a server would still require the server to have graphics and an awesome GPU where as a hypervisor would not. It's such a complicated subject to me. I guess I still have a lot of research to do.

As far as the server with no GUI, it is that way so it doesn't use a bunch or resources. You can add a GUI to your server by installing the desktop and xorg packages but it kind of defeats the purpose I think.

---

### Post by hankyknot on 2009-11-04
This is where I'm struggling. You may be right.

I took an old HP Server I had and installed Ubuntu 8.04 on it. I then installed the latest VirtualBox and then created two virtual machines both running Server 2003. They seem to run fine. Neither of them are high demand servers but I have to admit to being impressed with the speed.

I can manipulate and restart the servers totally independently. 

My terminology may be a little off as I am new to the whole virtualization thing. My understanding is that XenServer is a bare-metal hypervisor in that it doesn't need to sit on an OS. I refer to VirtualBox as a hypervisor because it takes the hardware as discovered and configured by the OS and creates a virtual environment in which I can construct virtual machines that are hardware independant.

My ideas are based around the fact that Ubuntu is a quick install and transporting virtual machines is relatively easy. Therefor as long as I have a current image or clone of a hard disk, in the event of a major hardware failure I can rebuild a Ubuntu box and restore an image very quickly.

Thats my understanding of it and if anyone can correct my understandings if they are wrong then that would be great.

---

### Post by Bölvaður on 2009-11-04
I suggest you take a look at custom made ubuntu projects like Masonux where you get pretty much what **you **will need but nothing more than that.

Most of the custom *thingies* have something else than gnome, which might be foreign to you. But your computer will have less overhead and therefore saving you perhaps up to 5p per year.

---

