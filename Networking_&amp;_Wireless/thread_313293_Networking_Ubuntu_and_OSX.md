---
title: "Networking Ubuntu and OSX"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by ign on 2006-12-05
i want to configure a small home network using two macbook pro laptops (osx 10.4) and a pentium iv running ubuntu.

i want to store all the multimedia files, photos and documents in the linux machine, plus use it for downloads, the two macs should be able to read and write files on that machine, share a printer and also control the downloads (i read that i can use control azureus through a net browser on a network). the macs would be connected through wireless and the linux box using ethernet. i have used ubuntu for a year or so, but i don't have any experience on networking.

if you can give me a hint on how to solve this i'd be extremely grateful!

---

### Post by IYY on 2006-12-05
I'd suggest using NFS, which is native to Linux and is supported by Mac OS. Another option is SAMBA, which also works with Windows.

System > Administration > Shared Folders

---

### Post by ign on 2006-12-06
thanks ivy, i'll have a look. will samba let me share a printer too? do you know a how-to i could use to begin with'

---

### Post by ign on 2007-08-24
i'm back with this project (home linux media/file server for use with mac osx laptops), i left it aside a while ago because i couldn't find a nfs guide that made me feel comfortable (it's my first experience with a server, i've used ubuntu desktop for a while, but i'm far from being an advanced user).
the question is if anybody around here has done a similar project and wants to share his/her experience or can point to an easy nfs guide.
another question would be about the difference between using nfs and samba. i know samba is a lot easier to use, but slower.

---

### Post by ign on 2007-08-27
if there is anyone else interested in building a home media server using ubuntu and accesing files on a mac (it should work the same with a win pc), i found a very detailed and easy howto here:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
right now my problem is that when i try to see videos located on the server using my laptop they stop from time to time, so it's a bit annoying. must be that the network isn't fast enough. i'm looking for a way to stream the videos on the server to the laptop in an easy way (preferably on samba, which is what i'm using right now). 
any ideas?

---

