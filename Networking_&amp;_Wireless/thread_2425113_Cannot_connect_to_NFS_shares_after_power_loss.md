---
title: "Cannot connect to NFS shares after power loss"
date: 2019-08-20
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2019-08-20
I have Ubuntu 18.04.3 x64 on 2 PC's in my house.  I have an NFSv3 setup to allow backups both locally and remotely to the shares.  Everything worked fine until I had a power failure this weekend.  When power failures occur, I always have to go to the server and issue the following 2 commands:```
sudo exportfs -ra
sudo restart nfs-kernel-server
```I did that once the 2 systems were back up.  I then entered at the client the following;```
sudo mount -a
```Unlike what has happened in the past when I issue > mount -aand 2 shares are mounted to my client, this time I received the following after a long wait:```
mount.nfs: Connection timed out
mount.nfs: Connection timed out
```I then checked my router to see if anything had changed.  It had not, but I rebooted it just in case.  Same problem.

I then enter the following commands with the indicated results (cp2 is my server name):```
~$ avahi-resolve-host-name cp2.local
cp2.local	fe80::2ca9:8cf:748f:af16
```
```
~$ ping cp2.local
PING cp2.local (192.168.1.174) 56(84) bytes of data.
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=1 ttl=64 time=0.248 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=2 ttl=64 time=0.408 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=3 ttl=64 time=0.333 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=4 ttl=64 time=0.254 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=5 ttl=64 time=0.339 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=6 ttl=64 time=0.305 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=7 ttl=64 time=0.409 msping cp2.local
PING cp2.local (192.168.1.174) 56(84) bytes of data.
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=1 ttl=64 time=0.248 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=2 ttl=64 time=0.408 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=3 ttl=64 time=0.333 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=4 ttl=64 time=0.254 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=5 ttl=64 time=0.339 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=6 ttl=64 time=0.305 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=7 ttl=64 time=0.409 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=8 ttl=64 time=0.419 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=9 ttl=64 time=0.343 msping cp2.local
PING cp2.local (192.168.1.174) 56(84) bytes of data.
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=1 ttl=64 time=0.248 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=2 ttl=64 time=0.408 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=3 ttl=64 time=0.333 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=4 ttl=64 time=0.254 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=5 ttl=64 time=0.339 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=6 ttl=64 time=0.305 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=7 ttl=64 time=0.409 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=8 ttl=64 time=0.419 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=9 ttl=64 time=0.343 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=10 ttl=64 time=0.388 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=11 ttl=64 time=0.387 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=12 ttl=64 time=0.343 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=13 ttl=64 time=0.210 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=14 ttl=64 time=0.347 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=15 ttl=64 time=0.366 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=16 ttl=64 time=0.373 ms
64 bytes from 192.168.1.174 (192.168.1.174): icmp_seq=17 ttl=64 time=0.388 ms
^Z
[1]+  Stopped                 ping cp2.local
```
```
~$ rpcinfo -p cp2.local
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100005    1   udp  33562  mountd
    100005    1   tcp  52421  mountd
    100005    2   udp  54443  mountd
    100005    2   tcp  38091  mountd
    100005    3   udp  45278  mountd
    100005    3   tcp  40519  mountd
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    3   tcp   2049
    100003    3   udp   2049  nfs
    100227    3   udp   2049
    100021    1   udp  52606  nlockmgr
    100021    3   udp  52606  nlockmgr
    100021    4   udp  52606  nlockmgr
    100021    1   tcp  46449  nlockmgr
    100021    3   tcp  46449  nlockmgr
    100021    4   tcp  46449  nlockmgr
```
```
~$ showmount -e cp2.local
Export list for cp2.local:
/media/brenda/Ubuntu_Data_Backup 192.168.1.0/24
/media/brenda/cp2_data           192.168.1.0/24
```
```
~$ sudo mount -a
mount.nfs: Connection timed out
mount.nfs: Connection timed out
```
```
~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=16423924k,nr_inodes=4105981,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3289560k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,stripe=32750)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=1352)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/core_7270.snap on /snap/core/7270 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_7396.snap on /snap/core/7396 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_81.snap on /snap/canonical-livepatch/81 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_77.snap on /snap/canonical-livepatch/77 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sde1 on /media/Data type ext4 (rw,relatime,errors=remount-ro)
/dev/sdc1 on /media/Data_Two type ext4 (rw,relatime,errors=remount-ro,stripe=32742)
/dev/sdb1 on /media/Data_Three type ext4 (rw,relatime,errors=remount-ro)
/dev/sdd1 on /media/Data_One type ext4 (rw,relatime,errors=remount-ro)
/dev/sdf1 on /media/butch/Ubuntu_Data_Back type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=3289560k,mode=755)
nsfs on /run/snapd/ns/canonical-livepatch.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=3289556k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdg1 on /media/butch/NTFS_Work type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_perm~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=16423924k,nr_inodes=4105981,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3289560k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,stripe=32750)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=1352)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/core_7270.snap on /snap/core/7270 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_7396.snap on /snap/core/7396 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_81.snap on /snap/canonical-livepatch/81 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_77.snap on /snap/canonical-livepatch/77 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sde1 on /media/Data type ext4 (rw,relatime,errors=remount-ro)
/dev/sdc1 on /media/Data_Two type ext4 (rw,relatime,errors=remount-ro,stripe=32742)
/dev/sdb1 on /media/Data_Three type ext4 (rw,relatime,errors=remount-ro)
/dev/sdd1 on /media/Data_One type ext4 (rw,relatime,errors=remount-ro)
/dev/sdf1 on /media/butch/Ubuntu_Data_Back type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=3289560k,mode=755)
nsfs on /run/snapd/ns/canonical-livepatch.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=3289556k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdg1 on /media/butch/NTFS_Work type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)issions,allow_other,blksize=4096,uhelper=udisks2)
```So, my router sees my 2 PC's on the LAN, my share exports are correct, I can ping the NFS server, I have started the nfs-kernel-server on the server, but I cannot connect to my NFS shares.  I am in need of help.

BTW, I did notice an nsfs that was from a snapd install that had never been there before.  Could this be the culprit?  If so, how do I get rid of it safely?  I think it came due to Livepatch.  If so, I'll disable Livepatch and get rid of all the snapd updates.

---

### Post by TheFu on 2019-08-20
I haven't a clue what the issue could be.  I've always tightly managed my internal network.  Perhaps you'll find something in my list that might help?  Maybe start by using IP addresses for everything on the client side?

Here's what I do.  
* My servers have static IPs.  PERIOD.
* I don't use avahi. EVER. purged the packages.
* Clients have static IPs, if they aren't portable devices, setup just like servers in config files. For NFS clients, I use **autofs**.
* Portable devices have DHCP reservations controlled by a dhcp server ... effectively static IPs.
* All the IPs on the subnet are in the /etc/hosts files on every device.  Ansible makes this easy for all, except the wired Android and Windows devices.  No wifi allowed on the same subnet.
* The /etc/exports on the NFS servers use specific hostnames. 1 entry for each host.  I've never done subnet-wide NFS exports.
* I disable kernel support for IPv6 completely.  Only IPv4. I'm not confident I can secure IPv6 properly. This includes disabling IPv6 on Windows.

I don't have any snaps.  The snapd package is purged.  If I need a container, then I'll set up a container or use firejail for a quick, light, solution. Being forced isn't cool.

If there was a power spike, then network cards and network ports on switches and routers could be fried.  Maybe try to move some of the physical port connections around? See if that helps.

---

### Post by cscj01 on 2019-08-20
I have resolved this problem, but I don't understand why it occurred.  My /etc/fstab has the following lines in it for defining my shares:```
#Entry for NFS Server on drive g on cp2
192.168.1.2:/media/brenda/Ubuntu_Data_Backup /nfs/Ubuntu_Data_Backup nfs _netdev,vers=3 0 0
#Entry for NFS Server shared documents on cp2
192.168.1.2:/media/brenda/cp2_data /nfs/cp2_shared_docs nfs _netdev,vers=3 0 0
```

I just checked my router configuration again, and the address is now 192.168.1.174 rather than 192.168.1.2.  So I changed the address in /etc/fstab and issued```
sudo mount -a
```and Voilà!

Now how did this change since it is always been 192.168.1.2 since I set it up years ago?  Suddenly, after a power failure I get assigned a new address?  And it never changed after previous power failures?

---

### Post by TheFu on 2019-08-20
Setup static IPs.  No more issues like that.

---

### Post by him610 on 2019-08-20
cscj01,
If your systems are subject to frequent power loss, you may wish to consider an uninterruptible power supply (UPS) for each system.

---

### Post by cscj01 on 2019-08-20
> **TheFu said:**
> Setup static IPs.  No more issues like that.

I guess I thought I had done so, but obviously not.  I just wonder how I got the same address all these years.  I will do so after this episode.

---

### Post by SeijiSensei on 2019-08-21
If you have multiple networked systems, the apcupsd utility with an APC power supply can inform the other machines on the network about an outage so they can all shut down cleanly.

---

### Post by TheFu on 2019-08-21
> **cscj01 said:**
> I guess I thought I had done so, but obviously not.  I just wonder how I got the same address all these years.  I will do so after this episode.

DHCP has a lease period.  If the router is on and the computer is off/rebooted and the lease hasn't expired, then it will get the same IP back.  If the PC is on and the router is rebooted, the PC will retain the leased IP until it expires, then request renewal from the DHCP server (router).  If the lease expires on the PC and the router are off, both will be fresh and get whatever IP lease is provided based on the DHCP server algorithm which might be random within a DHCP range or sequential within a DHCP range.

For non-portable devices, setting up static IPs on them directly means never wondering.
For portable devices, you might want to setup DHCP Reservations, which make the device effectively have a static IP on your LAN, but pick up normal DHCP settings elsewhere.
[https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) attempts to explain in more detail, but it doesn't say how to do YOUR router setup. They are all different and some don't support it.

The main trick is to keep reserved IP addresses outside the DHCP dynamic lease range.  So, if the DHCP server IP range is set to give out IPs from .200 to .254, then you want your static IPs and DHCP Reservations to be from .1 to .199.  Don't let those ranges cross. I'm assuming you have a /24 subnet  (255.255.255.0 netmask). This is very common in small networks.

I need to check out apcupsd.  My two 1500VA UPSes only tell the main physical systems connected to power down, not all the systems they power.

---

### Post by litasukar on 2019-08-22
**Run all commands in these steps from the ESXi/ESX command line with root access.**


Ensure that you can ping and vmkping the NFS server address.
Ensure that any firewalls between the ESX host and NFS Server do not block the connection.
Ensure the access on the NFS server is set to Anonymous user, Root Access (no_root_squash), and Read/Write.
Restore the mount with this command: 
Check to see if the datastore has mounted after trying to restore it with:
If it is not mounted, try remounting it using this command:
Open firewall ports on the network for RPC protocol and check the physical switch for any RPC protocol filtering.

---

