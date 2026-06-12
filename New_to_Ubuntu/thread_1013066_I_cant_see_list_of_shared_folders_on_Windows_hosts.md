---
title: "I cant see list of shared folders on Windows hosts from Ubuntu"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by mshadmehr on 2008-12-16
Hello there,

I am absolutely new in Ubuntu and just have Ubuntu 8.10 installed  on my laptop. When I started to play with it, everything seems to be work fine, until I get caught by a weird problem. 

When I try to connect to a network share on a Windows host, for example smb://desktop/videos/ it works fine, but if I just type smb://desktop/ it wont. In a Windows system it will list shared folders on that host, but in Ubuntu it is only a blank screen. I don't know if its normal behavior of Ubuntu or something is wrong? 

Can any body help me on this please?

Thanks,
Shadmehr

---

### Post by Hospadar on 2008-12-16
I think windows handles how the shares work a little differently.  Even in windows I've noticed sometimes similar issues depending on how I access the smb share.  In your example above, which share is the one actually being shared by windows?

---

### Post by mshadmehr on 2008-12-16
Sorry, but I didn't get your point.
When on a Windows system on the same network I open an Explorer window and type "\\desktop" in it's address bar, I get list of folders shared on that computer. In my case there are "videos", "mp3" and "documents". But on my Ubuntu laptop, when I open a File Browser window and type "smb://desktop/" in it's location bar, it remains empty. But if I type "smb://desktop/videos" or "smb://desktop/mp3" I will see list of files and directories inside it without any problem. So, I known this is not a permission issue nor a firewall issue. But I don't know how to fix it.

---

### Post by doobiest on 2008-12-16
What happens when you go into the ubuntu menu, then places, then network, windows network, etc.. does it eventually show up there?


Also from a terminal do smbtree to scan your network

---

### Post by mshadmehr on 2008-12-17
doobiest,

I tried smbtree, and it shows the other computer network shares without any problem. So what is File Browser's problem?

---

### Post by doobiest on 2008-12-17
OK so you can see it through smbtree but not in the nautilus?

From what I read it sound like you're trying to type in the direct path to the windows box. I was curious if you could browse to it by not typing in the path, rather using some mouse actions to double click your way through your network shares.

Have you also tried typing in the IP instead of hostname?

Just wondering if it less of a share discovery issue and more of a name resolution error.  I have an issue at home where I cannot type in my servers host name to browse directly to it's shares, but I can type in the IP and I can browse to it through Places > Network.

**Addtionally sorry I forgot that you can type in the hostname/sharename and that works so it's likely not a name resolution issue.

---

### Post by mshadmehr on 2008-12-18
> **doobiest said:**
> **Addtionally sorry I forgot that you can type in the hostname/sharename and that works so it's likely not a name resolution issue.

Yes, it works that way. Anyway, thank you for your time. I will continue to play with it and will try to test it with other computer/network to see if I can find the problem or not.

---

### Post by Kellemora on 2008-12-18
Hi MSH

Don't go messing around changing things!!!!!

There is a bug in Ubuntu where some days Places/Network shows the shares and other days it don't.  Been there and unresolved for like over 2 years now!

If you can see the computer and all the shares using smbtree, then everything is set correctly already.
You should be able to ping with no problem.
You should be able to use Go/Location and type the IP # no problem.
Sometimes using the path to share name will work, sometimes it won't, and if you haven't changed anything, and it works one day and not the next, there is NOTHING YOU can change that will make any difference.  It's part of the bug!

Other than perhaps try to reboot three times in quick succession, allowing for a full reboot of course.
This will sometimes allow the shares to show in Places/Network, sometimes not.

I thought one of the recent updates repaired this problem, finally.  Looks like perhaps not for everyone!

TTUL
Gary

---

