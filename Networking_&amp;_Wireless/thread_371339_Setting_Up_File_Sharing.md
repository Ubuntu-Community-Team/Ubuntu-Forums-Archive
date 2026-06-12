---
title: "Setting Up File Sharing"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by baboa on 2007-02-26
I am new to Linux, but not to computers. I am trying to get my G5 imac (w/Tiger) and my Ubuntu (Edgy) Box to play nice and share files. The Ubuntu machine is wired into my wireless router (Linksys wrt54gs), and my mac is connected to the router by wireless. I want to use my Ubuntu box  as a backup for the Mac (photos,music,etc...) Be gentle! I am just learning! ;) I should mention my Ubuntu box is a P4 (old windows box) :))

---

### Post by kidders on 2007-02-27
Hi there,

Although OSX and Linux share compatibility with several filesharing protocols, it probably makes the most sense to use Apple's one ... assuming the only machines you're interested in sharing with *are* Apples. Once Windoze enters the equation, you really only have one realistic option (MS filesharing, and all the silly irritations that go with it).

If Macs are what you're used to, then you're probably already familiar with AFP, so I would go for that. Other options that will work with Macs out of the box include Samba, WebDAV, and to a lesser extent (ie only if you're not an OSX novice), NFS.

---

### Post by baboa on 2007-02-27
I have samba set up in ubuntu, but I guess my problem is that the mac doesn't "appear" anywhere in Ubuntu. And though I can see it in the "network" pane of OSX, I can't connect. It keeps asking for name and password. I didn't think I had my share file set for that. In any case nothing I type into those fields works. (SIGH) If I did by mistake set up password access to my shared files in Ubuntu, how do I get rid of it? LOL

---

### Post by kidders on 2007-02-28
Hey again,

> **baboa said:**
> I have samba set up in ubuntu, but I guess my problem is that the mac doesn't "appear" anywhere in Ubuntu.

Your Mac uses Samba, just like your Ubuntu box, so it works almost identically. Depending on how familiar you are with the Windoze networking protocols, you may be able to diagnose your problem in terms of workgroup membership, local master browser elections, WINS settings, and so on. If you alter your Mac's smb.conf, be sure to make *small* changes, rather than radical overhauls. Afaik, "sudo killall"-ing all Samba-related processes will then cause OSX to restart Samba automatically, the next time you do something that requires it.

> **baboa said:**
> If I did by mistake set up password access to my shared files in Ubuntu, how do I get rid of it?Aside from being unsafe, doing that makes life quite difficult. If you don't authenticate when you access a Samba share, Ubuntu will have no idea what file access permissions to assign to things you create, or be able to distinguish between things *you* can access, that others can't. In addition, you would be unable to use the [homes] share.

Samba stores its own copies of users' passwords, so they can be managed separately from the rest of your system (which is handy for domain management, etc.). There are plenty of HOWTOs on this forum, and elsewhere, on various ways of setting Samba accounts up. :-) OSX can then store your access details in your keychain, so you can forget user authentication is even happening.

---

