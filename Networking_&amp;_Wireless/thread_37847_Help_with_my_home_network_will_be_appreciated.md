---
title: "Help with my home network will be appreciated"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by daageep on 2005-05-28
One of my beginning posts in this community.  :)  I hope someone can help me out with my problem(s). I've been trying to fix this annoying networking problem for a few days now and no luck.

Problem: I can't get the file sharing to work with two Ubuntu Hoary machines (one has only Hoary and one is dual boot of XP and Hoary) with a DLink DI-604 router. Each computer's internet is working and on the network (has a local IP for both comps). Both computers are on the same samba workgroup when I run /etc/samba/smb.conf and testparm has no errors. 

For some reason, when I click on "network servers" I don't see the other computer. In the "Windows Network" folder, I don't see anything either. This is true of both machines. Both machines have confirmed folders being shared.

Also, when I run smb://192.168.0.102/music, I get the following output: bash: smb://192.168.0.103/music: No such file or directory. The machines can ping either but cannot see/access eachother. When I boot into XP on the other machine, it can't see the other Ubuntu computer either.

But for some reason, *sometimes* I see one of my machines under Network servers. I'm thinking this has something to do with my DMZ settings (which i think is directed at the computer that I can see *sometimes*). I've followed all the instructions on the Ubuntuguide for networking, but commands work for me.

Please someone help! thank you

---

### Post by netrattler on 2005-05-28
Could you post a copy of your /etc/samba/smb.conf and I'll match it up to mine and see if I can find anything wrong with it.

Joe

---

