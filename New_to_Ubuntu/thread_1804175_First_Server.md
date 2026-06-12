---
title: "First Server"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by duke66 on 2011-07-14
So I have an old Sony VAIO desktop. Originally came with XP.  My goal with this is to turn it in to a server that I can access from anywhere and download whatever is on it. Very basic server functionality.

It would be hooked up to my personal LAN at home.  I'm just looking for settings that i should be aware of.

Currently I am reading through the Ubuntu 11.04 Server Guide just to get an idea of what to expect. As for previous experience with Unbuntu/Linux I have used Ubuntu 10.04 and Mint 11.

Links and any advice would be greatly appreciated.

---

### Post by androssofer on 2011-07-14
Hi, i hav sumthin similar (i think) with an eeebox.

not sure what exactly you want.. so will cover wot i did..

first i set up an ssh server on mine, which covers accessing it from anywer and transfers and even vnc can go through it!

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

then i would forward the ports on my lan to the computers. port 22 is default ssh, but another like 2222 is prob slighty more secure. the link for this would be specific to your router. but just google "port forwarding on **insert router name**"

then i would get a dynamic host name from dyndns.org... and set my computer to update tht, so u dont have to worry about what your ip is should ur ISP decided its needs changing..

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)


once you got those done the world is ur oyster... you can access ur files via ssh and transfer them using scp or sftp.

---

