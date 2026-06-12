---
title: "NFS woes. need help to debug."
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by bilbobagginz on 2007-09-03
Hi.
I have an NFS server, Debian Etch.
The server runs a software RAID, gives about 180 MB/s local throughput.
server exports a folder to the local /24 network as follows in /etc/exports:
/linux/homes xxx.xxx.xxx.0/24(rw,sync,no_subtree_check)
/linux/intel/local xxx.xxx.xxx..0/24(ro,async,no_subtree_check)

There is about 100 clients.
The network is a mix of 1000Mb and 100Mb ( nfs server is connected to a 1G link )

clients are:
Debian Etch 4.0
Ubuntu 7.04
mounting the /home as follows:

mynfsserver:/linux/homes /home nfs rw,tcp,mountvers=3,intr 0 1
mynfsserver:/linux/intel/local /usr/local nfs ro,tcp,mountvers=3,async,intr 0    0


The initial mounts work.
Problem #1:
 when I am trying to read a large file, like several MB, the clients stop "seeing" the server, although the server barely feels any load.
the client's load average creeps like hell, and it becomes unresponsive to input.
then the client needs to be reset.

Problem #2:
When a client on a slow link attempts to transfer files from the NFS mounted folder, via SFTP/SCP, the  SSH server ( i.e. NFS client ) also has the same effect.

Please help me to debug this problem, where to look for.

Thanks in advance!

---

### Post by Jose Catre-Vandis on 2007-09-03
For lines in /etc/exports, I use the following:

/linux/homes xxx.xxx.xxx.1/24(rw,no_root_squash,async)

and for the mounts:

mynfsserver:/linux/homes /homes nfs rsize=8192,wsize=8192,timeo=14,intr

I can shunt big files around no problem


Don't know if this would make any difference?

---

### Post by bilbobagginz on 2007-09-03
Hi, Jose. Thank you for the suggestion!
"I will try it", of course, but what I would like is to understand what is wrong in my setup.

How many clients do you have ?

Thanks in advance,
M.

---

### Post by Jose Catre-Vandis on 2007-09-03
Only 7, and not using nfs for steering users at their home directories either :), simply for file sharing, but it works :)

---

### Post by bilbobagginz on 2007-09-03
it seems this, most recommended setting allows me to run the 100 clients.

I will further investigate this issue.

what a voodoo this NFS is.

---

