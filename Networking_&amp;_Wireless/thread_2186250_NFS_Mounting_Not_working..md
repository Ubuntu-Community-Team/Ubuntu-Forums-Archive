---
title: "NFS Mounting Not working."
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-11-06
Sorry, all returns were delete when I posted.

I downgraded to Ubuntu 12.04 on the client because I thought there was a bug in 13.10 that prevented NFS mounting. After doing so, I still have the problem of the mount command hanging when mounting and nfs share. I have read and re-read the installation  and setup instruction ( [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo))  I have check and recheck that I have everything correctly setup. I have also turn off the firewall on both the client and the server.


 Exports file
```
/srv/pxeboot           192.168.1.2(rw,no_root_squash,async,insecure,subtree_check)
/srv/pxeboot/Images  192.168.1.2(ro,no_root_squash,async,subtree_check
```)


NFS-COMMON
```
NEED_STATD=STATDOPTS=NEED_GSSD=
NEED_IDMAPD=yes    was set just in case.
NFS-KERNEL-SERVERRPCNFSDCOUNT=8
RPCNFSDPRIORITY=0RPCMOUNTDOPTS="--manage-gids --debug all"
NEED_SVCGSSD=noRPCSVCGSSDOPTS=
RPCNFSDOPTS=
```


IDMAPD.CONF
```
Nobody-User = nobody
Nobody-Group = nogroup
LDAP and PORTMAP  are not being used.  
rpcinfo &#8211;p on server.  
 program vers proto   port  service    
100000    4   tcp    111  portmapper    
100000    3   tcp    111  portmapper   
 100000    2   tcp    111  portmapper    
100000    4   udp    111  portmapper    
100000    3   udp    111  portmapper    
100000    2   udp    111  portmapper    
100024    1   udp  42281  status    
100024    1   tcp  39329  status    
100003    2   tcp   2049  nfs    
100003    3   tcp   2049  nfs    
100003    4   tcp   2049  nfs    
100227    2   tcp   2049    
100227    3   tcp   2049    
100003    2   udp   2049  nfs    
100003    3   udp   2049  nfs    
100003    4   udp   2049  nfs    
100227    2   udp   2049    
100227    3   udp   2049    
100021    1   udp  37656  nlockmgr    
100021    3   udp  37656  nlockmgr    
100021    4   udp  37656  nlockmgr    
100021    1   tcp  47639  nlockmgr    
100021    3   tcp  47639  nlockmgr    
100021    4   tcp  47639  nlockmgr    
100005    1   udp  55095  mountd    
100005    1   tcp  35251  mountd    
100005    2   udp  33179  mountd    
100005    2   tcp  58952  mountd    
100005    3   udp  34450  mountd    
100005    3   tcp  33400  mountd
```


```
/proc/mount
srootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=8154788k,nr_inodes=2038697,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=3266868k,mode=755 0 0
/dev/disk/by-uuid/2291cc30-a7b3-4ed7-ae55-2299adcd1b9c / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw,relatime 0 0
//192.168.1.3/FileSync /mnt/FileSync cifs rw,relatime,vers=1.0,sec=ntlm,cache=loose,unc=\\192.168.1.3\FileSync,username=xbmc,uid=0,noforceuid,gid=0,noforcegid,addr=192.168.1.3,unix,posixpaths,serverino,acl,rsize=1048576,wsize=65536,actimeo=1 0 0
/dev/loop0 /srv/pxeboot/windows/8.1 udf ro,relatime,utf8 0 0/dev/loop1 /srv/pxeboot/Images/knoppix iso9660 ro,relatime 0 0nfsd /proc/fs/nfsd nfsd rw,relatime 0 0
/dev/disk/by-uuid/2291cc30-a7b3-4ed7-ae55-2299adcd1b9c /srv/pxeboot ext4 rw,relatime,errors=remount-ro,data=ordered 0 0/dev/disk/by-uuid/2291cc30-a7b3-4ed7-ae55-2299adcd1b9c /srv/pxeboot ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
```


NFS STATUS
$ /etc/init.d/nfs-kernel-server status
nfsd running


ps aux|grep nfs
```
root       776  0.0  0.0      0     0 ?        S<   Nov04   0:00 [nfsiod]
root     28157  0.0  0.0      0     0 ?        S<   13:26   0:00 [nfsd4]
root     28158  0.0  0.0      0     0 ?        S<   13:26   0:00 [nfsd4_callbacks]
root     28159  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28160  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28161  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28162  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28163  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28164  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28165  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
root     28166  0.0  0.0      0     0 ?        S    13:26   0:00 [nfsd]
xbmc     28417  0.0  0.0   9396   944 pts/3    S+   13:31   0:00 grep --color=auto nfs
```

```
xbmc@PlexOne:/srv$ ps aux |grep mountd
root     28170  0.0  0.0  24016  1092 ?        Ss   13:26   0:00 /usr/sbin/rpc.mountd --manage-gids --debug all
xbmc     28481  0.0  0.0   9392   944 pts/3    S+   13:33   0:00 grep --color=auto mountd

```
all I get in the client is this.
```
6 10:23:20 ubuntu kernel: [45979.892774] nfs: server 192.168.1.2 not responding, timed out
Nov  6 10:26:21 ubuntu kernel: [46161.083219] nfs: server 192.168.1.2 not responding, timed out
Nov  6 10:29:45 ubuntu kernel: [46364.282174] nfs: server 192.168.1.2 not responding, timed out
Nov  6 10:32:46 ubuntu kernel: [46545.472415] nfs: server 192.168.1.2 not responding, timed out
```


Hope someone can point me in the right direction. thanks.

---

### Post by ylafont on 2013-11-06
Unbelievable!    

After days of searching and checking and rechecking, I stumbled across this. [http://permalink.gmane.org/gmane.linux.nfsv4/11079](http://permalink.gmane.org/gmane.linux.nfsv4/11079)

> **ylafont said:**
> 
```
/srv/pxeboot           192.168.1.2(rw,no_root_squash,async,insecure,subtree_check)
/srv/pxeboot/Images  192.168.1.2(ro,no_root_squash,async,subtree_check
```)


I changed /etc/exports  to include the subnet. 

]/srv/pxeboot           192.168.1.2/255.255.255.0(rw,no_root_squash,async,insecure,subtree_check)
 /srv/pxeboot/Images  192.168.1.2/255.255.25..0(ro,no_root_squash,async,subtree_check[/CODE])

---

### Post by SeijiSensei on 2013-11-06
The IP address in /etc/exports does not mean what you seem to think it means.

It is not the address of the server, but a host or subnet address specification that includes valid clients.  So if you wanted all the machines in 192.168.1.0/24 to be able to use 192.168.1.2 as a server, the specification would read:

```

/srv/pxeboot         192.168.1.0/24(rw,no_root_squash,async,insecure,subtree_check)
/srv/pxeboot/Images  192.168.1.0/24(ro,no_root_squash,async,subtree_check)

```

It's also possible to have a network specification that differs from the host address itself.  For instance, you could replace the address spec above with 10.1.0.0/16 to permit access from any computers in that "class-B" subnet.  Usually if the server is handling multiple address specifications, you include separate lines in /etc/exports for each one.



Because of the way subnet numbering works, your method turns out to be equivalent to this one.

---

