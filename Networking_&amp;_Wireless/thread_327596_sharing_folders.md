---
title: "sharing folders"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by styven on 2006-12-29
Hi all,

I have read other threads on this and posted some of my problems.
As it stands i am stuck, so forgive me for starting a new thread in what i think is the right section.

My aim is to share my music folder to the other computers on my home network.
The location of this folder is home/styven/Music

I have installed nfs via......
sudo apt-get install portmap nfs-kernel-server

My laptop is the server machine 192.168.1.2

I have edited etc/exports to share /home/styven/Music

Please see screenshot.

I would like to know if i have done everything i should have done on the server machine.

The client is 192.168.1.3, i can ping between each machine.

I have installed nfs via.............
sudo apt-get install portmap nfs-common

I have also edited /etc/hosts.deny:
portmap : ALL
I have edited /etc/hosts.allow:
portmap : NFS server  192.168.1.3

I then carry out the following, and get these results on the client machine.............

honeyh@honey:~$ sudo /etc/init.d/nfs-common restart
Password:
* Stopping NFS common utilities [ ok ]
* Starting NFS common utilities [ ok ]
honeyh@honey:~$ sudo /etc/init.d/portmap restart
* Stopping portmap daemon... [ ok ]
* Starting portmap daemon... [ ok ]
honeyh@honey:~$ sudo gedit /etc/host.deny:
honeyh@honey:~$ sudo gedit /etc/host.allow:
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/Music
mount to NFS server '192.168.1.2' failed: server is down.
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/styven/Music
Password:
mount to NFS server '192.168.1.2' failed: server is down.
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/styven/Music
Password:
mount: 192.168.1.2:styven/Music failed, reason given by server: Permission denied
honeyh@honey:~$ sudo gedit /etc/host.allow:
honeyh@honey:~$ sudo mount 192.168.1.2:home/styven/Music /home/honeyh/styven/Music
mount: 192.168.1.2:home/styven/Music failed, reason given by server: Permission denied
honeyh@honey:~$

What have i done or not done?

Steve

---

### Post by simoncm on 2007-02-05
when using the mount on the client machine.  Use the full path to the files.

sudo mount (NFS server ip):/(full path) /(local client mount)

sudo mount 192.168.1.100:/home/desiredfolder /home/clientfolder

I had this issue and that was my solution.  Hope this helps a little!!

---

