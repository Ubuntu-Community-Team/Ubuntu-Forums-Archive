---
title: "iscsi Target"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by derek654 on 2010-03-04
I am a newbie to ubuntu. I have just installed an iscsitarget on ubuntu and am having problems connecting to it.  I can connect to it when I am in my LAN, but when I am trying to connect from a windows initator and a windows 7 machine it won't connect.  The main problem is that when I try to connect to that target, the target portal IP is the ip of the 192.168.2.55 local private ip and I can't find anywhere an option to change that to be my public ip.

I currently have my machine behind a router and is being natted.  

I am using port forwarding.

---

### Post by derek654 on 2010-03-07
What I mean is that when I am out of my LAN on my windows machine, the target portal thinks that it is the private ip that it wants to connect to.  I can't specify anything different.  If I change the ip address of my server, then that target portal ip changes as well.

---

