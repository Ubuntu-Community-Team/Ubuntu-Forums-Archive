---
title: "Trying to network"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-19
im trying to share files between 2 computers: 1 running Kubuntu 710 and 1 running Ubuntu 810. so far when i look under the "windows network" (smb:///) I see 2 networks 1 is called LinuxMCE which is my Kubuntu computer and 1 is called Workgroup which is my ubuntu computer. Ive shared the drives from both computers, but whenever I goto smb://linuxmce/ I dont see anything... this is driving me up a wall. anyone have any suggestions?

---

### Post by hyper_ch on 2008-12-19
if both are linux, why don't you just use sshfs to mount the other computer into your local filesystem?

---

### Post by Archer Troy on 2008-12-19
how do i do something like that?

---

### Post by hyper_ch on 2008-12-19
google helps:  [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by icecruncher on 2008-12-19
or use nfs. 
easy to set up. 

otherwise, do you have any firewalls in place?

---

### Post by porchrat on 2008-12-19
You sure it isn't something a little simpler, like a firewall issue?

---

### Post by Iowan on 2008-12-19
Does this one help?
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Archer Troy on 2008-12-19
smb://x.x.x.x where x.x.x.x is the ip of the windows machine

tried that -  all that comes up is a blank window.

the two computers are brand new installs so i don't think it should be a firewall issue.

Ive been trying to work through the nfs configuration,

on the guide im looking at, it says mount server.mydomain.com:/network"/officedoc"

([http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html))

I have no idea what my domain is though...where would i find what my domain is?

---

### Post by jerome1232 on 2008-12-19
Personally, I think ssh is the easiest method of sharing between two linux computers.

On the server (computer you want to connect to) Just install openssh-server either via synaptic (System-Admin-Synaptic) or apt-get
```
sudo apt-get install openssh-server
```
Then start the server
```
sudo /etc/init.d/ssh start
``` 

On the client (computer you want to connect from) Goto Places-Connect to server, select ssh, type in the ip of the server, and the username you want to connect as, then connect. It should get a shortcut placed on you desktop and you can bookmark for a permant places entry if you like.

---

### Post by Archer Troy on 2008-12-19
that...worked...awesome!

thanks for the help everyone. greatly appreciated.

---

