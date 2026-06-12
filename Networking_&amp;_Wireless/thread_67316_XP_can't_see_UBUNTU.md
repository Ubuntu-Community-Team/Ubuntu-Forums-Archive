---
title: "XP can't see UBUNTU"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by majkmil on 2005-09-19
I have a UBUNTU machine connected to my network through my router. I can print to the printer connected to one of the computers (all windows) directly. I can see all the other machines on the network from my UBUNTU computer. My problem is I can't see the UBUNTU comp from the Windows computers. Ubuntu comes up in EXPLORER, when I try to open the connection it says trying to connect to localhost@localdomain, this is in my HOST settings on UBUNTU. When I put in my password and usr name from my UBUNTU machine it won't connect. I think it is a permission issue but I can't figure it out. I could really use some help. Thanks Mark

---

### Post by OwenH on 2005-09-20
do you have nfs (network file system) set up on your ubuntu machine? I believe it comes with it out of the box 

some info on nfs and ubuntu:
[http://www.ubuntulinux.org/support/documentation/faq/nfs-server](http://www.ubuntulinux.org/support/documentation/faq/nfs-server)

samba is another option 

[http://us4.samba.org/samba/](http://us4.samba.org/samba/)

I havn't done this myself but good luck !

---

### Post by majkmil on 2005-09-20
Thanks for the reply. Not sure if NFS is the problem. When I go into network places the ubuntu comp shows up but says I can't change permissions because I am not the owner. Why does it think I am not the owner? This is the last thing I need to configure please help. Edit: would it help to get the latest samba?

---

### Post by OwenH on 2005-09-20
Sounds like when windows accesses the NFS share its messing with the file permissions,

does the directory that your sharing with NFS have at least read and write permissions on it for all groups? ie user, group and other ?

---

### Post by majkmil on 2005-09-20
Thanks,   Yes group and others have read rights, I just gave it write rights also.  When I open network servers my ubuntu comp as well as windows network. When I open windows network I get two workgroups. One shows ubuntu box and the other workgroup shows all the comps on the windows network ( which I can acsess ). I think my biggest problem is when I go to properties on the ubuntu machine in the network it says I am not the owmer and I cant change permissions, although read rightas are enabled for group and others. The other thing is I think windows can see me but only when I search for computers in explorer, but it asks foe password and usr name but I have tried both my ubuntu pass... and my windows pass... but nothing. Any help would be great.    Thanks

---

