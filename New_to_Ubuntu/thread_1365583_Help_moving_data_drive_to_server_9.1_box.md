---
title: "Help moving data drive to server 9.1 box"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by kodb on 2009-12-27
Hello all and thank you in advance as this is my first post here.
I am in the process of converting both our home and office networks to ubuntu 9.1 server/desktop environments and throwing away as much ms stuff as possible.  I've gotten a preliminary homeserver set up on an old HP P4 box with a 50G drive.  I have gotten samba and nfs set up and working.  My question is how do I take a 750G sata drive that has been sitting in a usb toaster to store our videos and move that drive into the inside of the server box (not via usb but via the sata connectors) so that I can share the video over the network?  Is this possible?  I searched and could not find an answer
Thanks again for helping this newb (Ubuntu)
KODB

---

### Post by Gone fishing on 2009-12-27
I don't think this will be a problem, you will need to add a line in fstab and mount it as something like /storage. Then share that with directory with NFS, the tell the client machined to mount at this at boot.

---

### Post by Daughain on 2009-12-27
Working on the assumption that you have all the proper connectors, you shouldn't have to do anything more than plug it in.

---

### Post by kodb on 2009-12-28
Solved; plugged in and then used nfs to share the drive.  Ended up using the usb toaster because connectors not compatible.
Had to edit the exports on the server and fstab on the clients
Thanks to all for their help!

---

