---
title: "new to xunbuntu"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by c_owl on 2008-04-04
hi all.
i have 5 computers all running xp pro, and i have been having problems getting my server up and running, my server is a 2200 amd athlon, 500mb ram, gig lan and 6tb harddrive space(12 drives). main use of this is file sharing on my network and torrent upload. the problem is with file sharing on the server, i have tryed ms server 2003 but it is to slow. i need some speed.
i have been told that unbuntu server would work perfect for what i need, but ive used xp for years and would not know were to start.
im used to gui but im willing to learn if it speed things up for me.
can anyone point me in the right direction with this
i use remote desktop a lot on my laptop to the other computers

any help would be great :confused::confused::confused:

---

### Post by jetsam on 2008-04-04
This tutorial covers setting up an xubuntu file server that does what you want and more:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1")

It was quite helpful to me when I was getting started.

You can just use it as a jumping off point.  I skipped the ftp and torrent stuff, and left the GUI on all the time because I sometimes use it for a second machine.

---

### Post by c_owl on 2008-04-04
thanks for that had a look at it seem ok.

this machine will be headless, so any pointers on how i can get this working. webmin was somthing i came accross but in very green when it comes to unbuntu.
but all i need is somthing to login to harddrive managing partioning and torrent checking

ill keep posting here to let u know how i get on.

thank again:)

---

### Post by c_owl on 2008-04-04
sorry reading on the link, i found that it is made headless.:(

---

### Post by c_owl on 2008-04-04
so what about harddrive managing i have 9 at 6 tb and need to login to manage the partions from remote
:confused:

---

### Post by jetsam on 2008-04-04
You should be able to use gparted over VNC to create new partitions.  

You'l need to mount them so the file system can access them.  This can get you started: 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c")

It's a bit out of date.  NTFS partitions can now be mounted read-write using ntfs-3g.  

If you're starting a partition from scratch, you'll get better performance and functionality using Linux's native ext3 filesystem instead of ntfs.  

I don't want to dissuade you, but you might consider installing and using Ubuntu as a desktop system for a week or two before diving into the deeper waters of setting up a server.  That way, you would   just have a learning curve to master instead of a learning cliff.

---

### Post by c_owl on 2008-04-04
thanks for that.
im still going to give it a shot with xunbuntu as ive been programming for years in vb. and im used to command lines for trouble shooting.

i know i need to learn this from scratch and i like a challenge.

:popcorn:

---

