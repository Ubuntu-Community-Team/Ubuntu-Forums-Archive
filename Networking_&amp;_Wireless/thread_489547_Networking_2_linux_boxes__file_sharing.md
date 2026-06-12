---
title: "Networking 2 linux boxes / file sharing"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by xSauronx on 2007-07-01
Ive currently got 2 laptops. 1, my old laptop, running Debian Etch, and the second that I recently bought, running Feisty. 

I want to network them together for the sake of transferring data from the old to the new. What options have I got for doing this and where can I go to learn more about them? 

Im interested in trying out a coupe of different things just for the sake of learning, so any suggestions are welcome. Ive done this before with a windows box and a linux box using samba...but I couldn't get it working *quite* right and just ran a simple FTP server on the windows box to help transfer everything. 

Thanks :)

---

### Post by baldercm on 2007-07-01
Hi!
If you're using Linux on your both computers, I suppose the best option you have is using NFS shares. NFS stands for Network File System. It allows you to mount a disk partition stored on a remote machine as if it were a local disk. You can find the NFS documentation here [http://nfs.sourceforge.net/nfs-howto/]("http://nfs.sourceforge.net/nfs-howto/"). I think you will have enough with chapters 3 and 4for setting up your home network. Basic configuration It's pretty easy, don't worry.

You need to install the package 'nfs-kernel-server' on any machine that you want to act as "share server", ie, you want the files on the machine shared on your network.

You need the package 'nfs-client' if you want a machine to be able to search and mount your nfs shares.

---

### Post by xSauronx on 2007-07-01
sweet

that took no time, thanks :)

---

### Post by randria62 on 2007-07-01
Hi,

I have a NFS server running Dapper sharing files over NFS to 6 clients and 1 laptop all running feisty. My problem is that the clients are not mounting the shared files automatically at boot time when I configure every client with a static IP. On the other hand, configuring each of the client with automatic DHCP IP gets them mount the files automatically. I absolutely need to configure each client with a static IP because with regular power offs we are losing the local network if a client is unable to retrieve an IP address. I am completely lost as I need to share files via NFS and need to configure static IP. Can anybody help?

Thx. Didier

---

