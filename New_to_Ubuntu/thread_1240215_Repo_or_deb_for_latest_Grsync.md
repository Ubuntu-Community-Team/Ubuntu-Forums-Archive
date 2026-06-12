---
title: "Repo or deb for latest Grsync?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-08-14
Hey guys,

I'm re-installing my system, and I just saw that there's a MUCH newer version of Grsync available than the one in the repos. In Synaptic, all I find is 0.6.1, but on the web page, the latest version is 0.9.1. I want it!

Problem: I can only find the source code. I've tried compiling programs from source in the past, it aaaaaaalways f%&#ed up something in my system and left me with a broken carcass of a program that I could not remove.

Does anybody know where I can find a .deb of the latest Grsync, or is there a repo?

Thanks!
M.

---

### Post by XCan on 2009-08-14
I think you may want to look into PPA, [https://launchpad.net/~bhavi/+archive/my-collections](https://launchpad.net/~bhavi/+archive/my-collections) . You will have to add that to your software sources, be aware though that if you trust it too much when it comes to drivers and stuff, you may screw up your system.

---

### Post by The Bright Side on 2009-08-14
Hwo do I add it? I added this line

deb [https://launchpad.net/~bhavi/+archive/my-collections](https://launchpad.net/~bhavi/+archive/my-collections) jaunty main

And I got the following error:

Failed to fetch [https://launchpad.net/~bhavi/+archive/my-collections/dists/jaunty/main/binary-amd64/Packages](https://launchpad.net/~bhavi/+archive/my-collections/dists/jaunty/main/binary-amd64/Packages)
The requested URL returned error: 404
Some index files failed to download, they have been ignored, or old ones used instead.

I know, I'm a total noob... Thanks!

---

### Post by philinux on 2009-08-14
[https://launchpad.net/~bhavi/+archive/my-collections](https://launchpad.net/~bhavi/+archive/my-collections)

Scroll down the page for the deb files.

[https://launchpad.net/~bhavi/+archive/my-collections/+files/grsync_0.9.1-1ubuntu1_i386.deb](https://launchpad.net/~bhavi/+archive/my-collections/+files/grsync_0.9.1-1ubuntu1_i386.deb)

---

### Post by The Bright Side on 2009-08-14
Thanks! The keyserver just died, but once it's accessible again, I'll give adding the PPA to my repositories a shot. When I download the .deb and execute it from Nautilus, I get this error:

Error: Dependency is not satisfiable: libgtk2.0-0 (>= 2.17.5)

I searched for libgtk in the Synaptic Package Manager, but I get a ton of search results, and none match exactly what is mentioned in the error.

---

### Post by philinux on 2009-08-14
Oh well thats because the installed versin of libgtk2.0-0 is version 2.16.1.

Cant help you with that.

---

