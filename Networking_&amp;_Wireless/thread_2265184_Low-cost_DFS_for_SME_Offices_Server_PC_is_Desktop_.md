---
title: "Low-cost DFS for SME Offices: Server PC is Desktop PC, Desktop PC is Server PC"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by hhtmp88 on 2015-02-13
Dear all,

I am not sure if this is possible:
Suppose a SME of 5 persons without any servers, each of them has his own Desktop PC with Hardware Config. as follows:
-- PC1: Celeron J1900 mini-ITX mainboard, with 2GB DDR3-1600 RAM, 2TB 3.5" SATA3 Harddisk
-- PC2, PC3: same config as PC1
-- PC4, PC5: same config as PC1,except that the 2TB Hardisk is replaced by a 64GB SSD
-- PC6: Remote PC located in another Office with the same config as PC1. The two offices are connected to internet thru broadband


PC1: Ubuntu 14.10 Desktop and a DFS (Distributed File System) are installed and configured 
-- Admin Account and Accounts of all the 5 users are created; -- Their resources and storage space are also assigned 
-- at this moment, no fault tolerance as there is only one PC


PC2: An USB Stick is created for auto-installation and auto-configuration for PC2 
-- at this moment, fault tolerance is added to the system as file replication will be performed by the DFS 
-- for load-balancing and faster access, user logged into this PC will access his own files physically stored in the Harddisk of PC2


PC3: The same USB Stick is used for auto-installation and auto-configuration of PC3 
-- for load-balancing and faster access, user logged into this PC will access his own files physically stored in the Harddisk of PC3


PC4: The same USB Stick is used for auto-installation and auto-configuration 
-- for load-balancing, user logged into this PC will access his own files physically stored in the Harddisk of PC2, unless PC2 is crashed


PC5: The same USB Stick is used for auto-installation and auto-configuration 
-- for load-balancing, user logged into this PC will access his own files physically stored in the Harddisk of PC3, unless PC3 is crashed


PC6: It is temporary connected to this office LAN. The same USB Stick is used for auto-installation and auto-configuration. It will be installed to the second office of the company. 
-- for load-balancing, user logged into this PC will access his own files physically stored in the Harddisk of PC6


If any of the above PC is crashed, simply remove it from the LAN, replaced with a new hardware, auto-install and auto-config it using that USB stick. -- so the system crash only if all the four PC's, PC1-PC3, and the remote PC, are crashed


My Questions:
1. Is there such an USB stick that can be made to perform all the task as stated above?

2. Is the above system practically feasible?
3. Which open-source DFS should I use to get the job done?

4. Fixed IP broadband must be used? Or I can used the much cheaper dynamic IP broadband connection?


Thanks for any kind of help and comments!Low-cost DFS for SME Offices: Server PC is Desktop PC, Desktop PC is Server PC

---

### Post by TheFu on 2015-02-13
1) anything is possible with enough time/budget/effort. Feel free.  LFS is
2) TL;dr - I wouldn't do it that way. Seemed way to complicated, but i DR.  Plus for these systems to find each other, they will need static IPs on the LAN. There are ways to do it via DHCP, but it will need to be done and every new machine will need to be pre-configured for a static IP on the LAN.
3) No idea. It really depends on how solid the networking is between the locations and how much you care about security, if at all. I wouldn't consider DSL and symmetric bandwidth would be highly recommended.
4) how much do you care about security? How much latency can you stand?  Storage isn't just storage. The exact use makes a difference.  Any DBs running, concurrent file editing, any block devices needed?

Lots of things are possible. That doesn't mean they are good ideas.  Installing from USB is fine for a small shop. Enterprises will install from a central PXE boot setup.  Just make certain that none of these locations uses the same or popular subnets.  That will screw with routing and VPNs ... don't use 192.168.0.0/24 or 192.168.1.0/24.  Probably best to use some odd subnets in the 10.x.x.x or 172.x.x.x ranges. Avoid collisions, right?

Most places create a "file server" and store files on it. Then replicate those files either with a DFS or through periodic replication - daily, every 8, 6, 4, 1 hour ... just depends. If block storage or DBMS storage is needed, things get more complex.  DFS like bandwidth between the locations - lots-o-bandwidth.  25Mbps symmetric would be suggested. Less can work, but it will be painful.

To try out remote storage access easily, check out sshfs. How does that work for you?  BTW, remote storage protocols don't always support all the normal things we use in a file system, so be aware of those limitations before you decide on the solution.

[http://serverfault.com/questions/193050/is-there-something-like-microsoft-windows-server-dfs-for-linux](http://serverfault.com/questions/193050/is-there-something-like-microsoft-windows-server-dfs-for-linux) says, Ceph, Lustre and gFarm are options for your consideration. Each has issues.

At home, I only use replication. This can help recover after any file corruption, if it is noticed quickly enough. Plus none of this removes the requirement for backups. Nothing replaces versioned backups. Nothing.

---

### Post by hhtmp88 on 2015-02-13
Thanks "TheFu" for your comments!

1. What is "LFS"? a software for making the wanted Installation USB stick?
2. I am not sure, but I believe "[heartbeat]("http://www.linux-ha.org/doc/users-guide/users-guide.html")" has to be added to PC1 to PC5, in order to make them synchronized on the OS aspect, while DFS is on the file storage aspect
3. What security aspect do you concerned? 
4. Concurrent file editing can be disabled. About the latency issue -- the system should be configured that user logged in a particular PC, e.g PC1, will access his own files physically stored in the harddisk of PC1


Welcome any further comments from you and anyone else!

---

### Post by hhtmp88 on 2015-02-28
I finally find this High Availability OS that may make things happen:
[https://pve.proxmox.com/wiki/High_Availability_Cluster](https://pve.proxmox.com/wiki/High_Availability_Cluster)

I also document this system here for future development purpose:
[http://kb.jinmy.me/view/Low-cost_DFS_for_SME_Offices](http://kb.jinmy.me/view/Low-cost_DFS_for_SME_Offices)

---

### Post by TheFu on 2015-02-28
Any pair of Ubuntu KVM hosts with libvirt can be made into a cluster like proxmox. That isn't to say that proxmox isn't nice. It has a pretty web GUI. A few of the moderators here use it. 

Proxmox is NOT a DFS - it is just a VM management tool and those VMs can be used for 1,000,000 of other purposes, including running a clustered file system - as mentioned above.

It doesn't meet your initial requirements, that's certain, but if you have bended on the requirements, there are many other options too.

Regardless, if it works for you, great!

---

