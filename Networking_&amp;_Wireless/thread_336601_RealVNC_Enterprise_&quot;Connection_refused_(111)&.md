---
title: "RealVNC Enterprise &quot;Connection refused (111)&quot;"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by volatile.memory on 2007-01-11
I've installed VNC on Ubuntu 6.10 using the instructions [here]("http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome"), with the exception that I installed realVNC Enterprise edition instead of vnc4server (downloaded and installed tarball).

I also installed a (temporary) license key (this is the Enterpri$e edition after all).

I've set everything else up according to the posts (I read the entire thread), but when trying the basic ```
$ vncviewer localhost:1
``` I get ```
VNC Viewer Enterprise Edition E4.2.7 for X - built Dec 22 2006 11:54:07
Copyright (C) 2002-2006 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.


Thu Jan 11 20:48:09 2007
 TcpSocket:   connect failed:unable to connect to host: Connection refused
              (111)
 main:        failed to connect: Connection refused (111)

```

I've  tried everything in the thread but it's still happening. I've also scoured the 'Net for others with a similar problem, but haven't come up with anything new.

Any ideas, fellow Ubuntuites?

Thanks in advance, 
v.m

---

### Post by lukemack on 2007-01-15
did you resolve this? if so how?

---

### Post by volatile.memory on 2007-01-15
Haven't resolved it yet. I'll dig into it some more, maybe post on the RealVNC list... in the meantime I'm still hoping for some help here, as this is a great forum. I'm really surprised no one has encountered this and posted a reply... normally this board is more responsive.

Regardless, I'll post something when I get it fixed (or give up).

v.m

---

### Post by lukemack on 2007-01-15
cool. having read around the subject a little, i'd say you havent installed or configured VNC correctly. or maybe you have used a version which is not supported on ubuntu? AMD64 users also need a patch i think.

anyway, for now i'm doing this:

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

you need to have installed ubuntu desktop on your server for this to work.

---

### Post by volatile.memory on 2007-01-15
I'm pretty sure it's a configuration issue, I'm just not sure what. Based on everything I've read, I should be good to go. Like I said, I'll do some more digging.

I can't use the built-in Vino server, since it requires an active session. I'm running a headless server, so remotely doing things like rebooting (which logs everyone off) would leave me helpless.

v.m

---

### Post by Kamran7860 on 2007-07-09
youve got the vnc servers enryption on switch it of and it should work.

---

### Post by krammer on 2007-07-22
How do you turn it off?

---

### Post by Jongi on 2007-07-25
krammer did you manage to switch it off?

---

