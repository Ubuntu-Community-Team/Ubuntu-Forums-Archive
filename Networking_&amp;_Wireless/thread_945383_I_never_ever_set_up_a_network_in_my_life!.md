---
title: "I never ever set up a network in my life!"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Cotopaxi on 2008-10-12
Hi,

I have desktop with Kubuntu Hardy and a laptop, also with Kubuntu Hardy. The router I have is a D-LINK DSL 504 T.

I have never ever set up a network. Essentially, what I want to do is be able to transfer files from my desktop to the laptop (and vice versa), so I have all files on my laptop when I travel.

I have root permission for both machines.

Thanks for your help!

---

### Post by iponeverything on 2008-10-12
install sshd on both machines


sudo apt-get install  openssh-server

then find the ip address of your machines:

ifconfig 

will give you that information.

then copy the files with scp:

from laptop to server:
```
scp files username@server-ip-address:Desktop/
```

---

### Post by sokopok on 2008-10-12
Might be more efficient just using NFS (if you're behind a router it's not acessible to the outside world anyway):
```
sudo apt-get install  nfs-kernel-server
```
and then use the gui tools in kde to setup sharing (right click the folder you want to share, choose properties and set appropriate options)
Or if you want to use SSH, you can access thes via Dolphin: in the address bar type: ```
fish://user@hostname/
```

---

