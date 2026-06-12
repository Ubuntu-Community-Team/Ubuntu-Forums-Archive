---
title: "NFS problem - Input Output Error"
date: 2005-09-28
forum: Networking &amp; Wireless
---

### Post by holiday on 2005-09-28
I have a user stephen on two linux boxes: a FC2 mongrel Desktop and 
a breezy toshiba laptop. I know this is not a breezy group but it's 
the only network group I could find. Please 

I'm trying to mount some FC2 directories as nfs, but am getting 
$ Input Output Error
on attempting to list the mounted directory.


This worked with my FC1 laptop 
so I'm fairly confident in the FC2 server setup.

After mounting, the FC2 directories are listed by 
the breezy mount;

# mount
192.168.0.100:/usr/local/share on /mnt/sroom/share type nfs (ro,soft,intr,addr=192.168.0.100)
192.168.0.100:/mnt/windows on /mnt/sroom/windows type nfs (ro,soft,intr,addr=192.168.0.100)
192.168.0.100:/home/stephen on /home/stephen/sroom type nfs (rw,soft,intr,addr=192.168.0.100)

but the permissions look wrong:

$ll /home/stephen | grep sroom
drwx------  92 stephen stephen  12K 2005-09-27 23:21 sroom

and attempting to list a mounted directory gives 

$ls /home/stephen/sroom
<hangs until I Ctl-z and then,..>
ls: reading directory /home/stephen/sroom: Input/output error

$dmesg
[12738.055622] nfs warning: mount version older than kernel
[13033.250611] nfs: server 192.168.0.100 not responding, timed out

My breezy is up to date.

uid.guid of stephen on both machines is 1000.1000


/etc/exports on FC2 server
#
/home/stephen 192.168.0.101(rw,sync)
/mnt/windows 192.168.0.101(ro,sync)
/usr/local/share 192.168.0.101(rw,sync)


/etc/fstab on breezy client 
192.168.0.100:/usr/local/share  /mnt/sroom/share   nfs ro,soft,intr 0       0
192.168.0.100:/mnt/windows      /mnt/sroom/windows nfs ro,soft,intr 0       0
192.168.0.100:/home/stephen     /home/stephen/sroom nfs rw,soft,intr 0       0

rpcinfo agrees - both ways, and shows portmapper with identical 
entries on both sides.

Perhas a significant diff: rpcinfo on the laptop does not have nfs.


100000    2   tcp    111  portmapper
100000    2   udp    111  portmapper
100021    1   udp  32768  nlockmgr
100021    3   udp  32768  nlockmgr
100021    4   udp  32768  nlockmgr
100021    1   tcp  32769  nlockmgr
100021    3   tcp  32769  nlockmgr
100021    4   tcp  32769  nlockmgr
100024    1   udp   1005  status
100024    1   tcp   1008  status

I've been working on this a while.

---

