---
title: "NFS problem with server"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by ptgood on 2008-07-04
I set up an home network with two clients and one server (running Xubuntu and Ubuntu).

I followed this HOW TO: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

Everything worked fine, but when i restarted the three machines, i had to restart manually the server kernel with:
[I][B][LIST]
[*]sudo /etc/init.d/nfs-kernel-server restart
[/LIST][/B][/I]
If i dont do that, when i try to mount the folder from clients, i get this: 
[B][I][LIST]
[*]mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
[/LIST][/I][/B]

Have you any idea?
why should i restart the server manually every time?

Thanks

---

### Post by zzatz on 2008-07-04
My guess is that NFS isn't automatically starting on boot on the server. That's usually handled by the System V init structure.

On the server, you should have directories in /etc for each run level. Look for /etc/rc1.d, /etc/rc2.d, and so on. Runlevel 0 is Halted, runlevel 1 is single user administrative mode, and runlevel 6 is reboot. Runlevels 2, 3,4, and 5 are normal multi-user runlevels. Most Linux distributions only use one of the multiuser levels, either 2 or 5.

Each sysv runlevel directory contains symbolic links to the startup scripts in /etc/init.d. A link starting with 'S' means 'start', and a link starting with 'K' means kill or shutdown. The digits that follow give the order in which the scripts are run. You can't start NFS until networking is running, for example.

The System>Administration>Services menu will let you select which service should run on boot. There are also command line tools for this; I don't recall which, if any, are installed by default. Try 'man -k sysv' and see if any are listed.

You can also create, edit, or delete the links by hand. If you have /etc/rc2.d/K20nfs-kernel-server, rename it to/etc/rc2.d/S20nfs-kernel-server. Sometimes brute force is easier.

---

### Post by ptgood on 2008-07-04
I LOVE YOU

I checked in /etc/rc2.d and there was not **nfs-kernel-server** at all.

So I opened /etc/init.d, I created a link of **nfs-kernel-server**, I renamed the link to **S20nfs-kernel-server** and I copied it in /etc/rc2.d

I rebooted the machines and everything work perfectly!!!

Thanks a lot, You're my Hero

---

### Post by zzatz on 2008-07-04
You'll want to make the appropriate links in each sysv directory. In other words, you want NFS to halt cleanly when you shut down, too.

The links should have been set up when the nfs-kernel-server package was installed. You can try 'dpkg-reconfigure nfs-kernel-server', or 'apt-get install --reinstall nfs-kernel-server'.

---

### Post by caprilo on 2009-12-13
Great! Thank you. There are literally thousands of threads talking about this around Google, but this simple thing was the problem.

---

### Post by rafe101 on 2010-07-26
Thanks, I was having trouble with this on my 10.04 myth box. I thought I had it fixed when I set the allowances to specifically mention the laptops, but it came back again. Reconfiguring the nfs server like you mentioned seems to have worked.

---

