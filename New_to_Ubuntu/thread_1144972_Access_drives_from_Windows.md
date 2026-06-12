---
title: "Access drives from Windows"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by restless-e on 2009-05-01
Okay so here's my situation: I'm trying to share my 2 external drives from my XP system over the network and be able to  stream my videos and audio onto a Jaunty system in my room.

I have the 2 drives already shared and I access them from my 2 laptops which are running xp and vista over the network no problem. 

I'm still a bit new to networking features on Ubuntu and am wondering how I would be able to access the drives or mount them on boot so I can watch my shows/movies on my LCD without having to drag my drives into the room. Both drives are formatted in NTSF if it matters.

I know this is probably simple but I have not been able to find an answer on any post, most people seem to have ubuntu hosting the files running samba while accessing them through windows. Any help or instructions on how to do this would be helpful, thanks!

~e

---

### Post by Cypher on 2009-05-01
Since you are sharing the drive over the network, the fact that it is NTFS doesn't matter. You will be using SAMBA on your Ubuntu machine to access the drive.

Open up file browser and under Network, you might see your workgroup that the Windows machine belong to, if so, you should be able to browse to the appropraite machine and already see the shares.

If that's true, then you can automatically mount the shares in Ubuntu using /etc/fstab.

[This howto]("http://ubuntuforums.org/showthread.php?t=280473") will help you with the specifics.

---

### Post by restless-e on 2009-05-01
Thank you very much for the response I'll defiantly try this out as soon as I get home from work, hopefully I'll be able to have it up and running by tonight!

---

