---
title: "Remote folders?"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by revenant138 on 2008-04-10
Hello all,

My girl and I want to be able to mount our movie/music folders to each other on bootup. I dont want to have to manually do anything, i want it to connect and mount the folder on boot. 

I was wondering if there is an accepted or recommended way of doing this. I've set it up with fuse once before but I thought there might be a more obvious way.

'hanx

---

### Post by notwen on 2008-04-10
Are you both running Ubuntu(or atleast Debian-based distros) ?  If you are then you could both use NFS to mount a shared folder on each other's machine.  Check out [this NFS guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server") on ubuntuguide.  You specify a mount point on your local(client) machine and it mounts the shared folder from the server machine in said mount point.  So if you are both sharing something from each other's machines, I would guess you would need to setup both the client & server on both machines.  You could then edit your /etc/fstab to mount each on startup(you may want to reserve internal ips for each machine on your router).  Post back if you go w/ this and have any questions.  

I use NFS to stream media from my file server to my laptops.  =]

---EDIT---
You may be stuck using Samba if you're needing to share folders/files between Linux & Windows machines.

---

### Post by revenant138 on 2008-04-10
Yes, we are both using Ubuntu Gutsy. Lol same hardware even, it was easy to build a second machine out of something i know worked :P

This sounds like the kind of solution I was looking for. I knew there had to be a way that made more sense. I will be trying this and posting my results.

Thanks!

---

