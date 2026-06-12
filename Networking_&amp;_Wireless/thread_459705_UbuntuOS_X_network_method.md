---
title: "Ubuntu/OS X network method"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by maeks84 on 2007-05-30
SSH, Samba, Netatalk, AFP, NFS, other......

I just don't know what to use.  All I need to do (for now) is connect to the Ubuntu (Feisty Fawn) computer from the Mac (OS X 10.3.9) via the Finder 'Connect to server' command.  I want access to the entire hard drive on the Ubuntu computer.  (May limit to certain directories later, but whole thing for now.)  With decent speed.  (I copied a file via the command line with SSH and it seemed to take quite a while.)

I would appreciate it if someone could recommend what protocol to use.  Just need to know what will accomplish what I need done, so I can focus on it and quit jumping back and forth trying to get something to work.  Thank-you

---

### Post by mbradlcu on 2007-05-31
nfs is very fast but it's best used behind a firewall. nfs is pretty easy to setup. just install nfs-kernel-server and what ever associated dependencies, then edit the /etc/exports file, here's an example:
> 
/home/satch     192.168.0.0/24(sync,rw,no_root_squash)

 On osx I use a free utility that works pretty well as I've had problems with the netinfo manager. here's the link to that software: [http://www.bresink.de/osx/NFSManager.html](http://www.bresink.de/osx/NFSManager.html)

---

### Post by maeks84 on 2007-05-31
Thank-you very much.  Will work on getting NFS to working.

---

