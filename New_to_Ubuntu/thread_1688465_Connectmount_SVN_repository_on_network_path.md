---
title: "Connect/mount SVN repository on network path"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Ubu-Newby on 2011-02-15
Hello,

I have just installed Ubuntu 10.10 on a VMWare Virtual machine under Windows Vista. Everything so far has gone amazingly smooth, but now here is my first problem: 

I can access the windows host PC using "network" in the file browser. However, I need to access it from the terminal (actually I have to connect to an SVN repository on the network path). When I switch to that network path in the file brower, then its location (under properties) is specified as

  smb://pc11/d/svn_repositories

I guess I have to somehow mount this path into my file tree to access it over the terminal. I tried some mount command but without success.  Basically my problem is that I don't know how to address this network location in the mount command. The above "smb:" syntay does not seem to work ...
Can anybody point me into the right direction?

Thanks Alot!

---

### Post by Ubu-Newby on 2011-02-15
Ok, after trying another hour I got it to working using the explicit IP address (found with nmblookup):


  sudo mkdir /mnt/svn
  sudo mount.cifs //192.168.32.2/svn_repositories /mnt/svn

---

