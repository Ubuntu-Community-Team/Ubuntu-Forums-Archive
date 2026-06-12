---
title: "Poor NFS4 Read Performance Since 20.10 Upgrade"
date: 2021-11-22
forum: Networking &amp; Wireless
---

### Post by CharlesT423 on 2021-11-22
I recently upgraded my two home boxes from Ubuntu 20.10 to 21.10 (groovy to impish I believe?) and ever since then my NFS read performance has gotten really bad.  One of my boxes is a home file server that I store my music and video content on, and I'm now getting buffering issues while fast forwarding through videos, or access to the music share will hang while a video is playing.  It seems to get worse if I have multiple files open at once.  IE, if I play a video on one screen and then open up another one and fast forward through it both videos will hang for a few seconds.  It's a gigabit network and I'm not seeing any interface errors or any retransmits in nfsiostat, This is what nfsstat -c shows on the client:

```

[FONT=monospace][COLOR=#000000]Client rpc stats: [/COLOR]
calls      retrans    authrefrsh 
620607     20         620577   

Client nfs v3: 
null             getattr          setattr          lookup           access            
62        0%     981       6%     0         0%     11487    73%     1255      8%      
readlink         read             write            create           mkdir             
38        0%     1027      6%     0         0%     0         0%     0         0%      
symlink          mknod            remove           rmdir            rename            
0         0%     0         0%     0         0%     0         0%     0         0%      
link             readdir          readdirplus      fsstat           fsinfo            
0         0%     0         0%     489       3%     5         0%     124       0%      
pathconf         commit            
62        0%     0         0%      

Client nfs v4: 
null             read             write            commit           open              
1         0%     445782   73%     181       0%     1         0%     1232      0%      
open_conf        open_noat        open_dgrd        close            setattr           
0         0%     5427      0%     128       0%     5196      0%     311       0%      
fsinfo           renew            setclntid        confirm          lock              
202       0%     0         0%     0         0%     0         0%     41        0%      
lockt            locku            access           getattr          lookup            
0         0%     41        0%     2301      0%     121231   20%     7996      1%      
lookup_root      remove           rename           link             symlink           
66        0%     115       0%     20        0%     0         0%     34        0%      
create           pathconf         statfs           readlink         readdir           
2         0%     136       0%     814       0%     22        0%     806       0%      
server_caps      delegreturn      getacl           setacl           fs_locations      
338       0%     4906      0%     0         0%     0         0%     0         0%      
rel_lkowner      secinfo          fsid_present     exchange_id      create_session    
0         0%     0         0%     0         0%     38        0%     73        0%      
destroy_session  sequence         get_lease_time   reclaim_comp     layoutget         
36        0%     7557      1%     36        0%     37        0%     0         0%      
getdevinfo       layoutcommit     layoutreturn     secinfo_no       test_stateid      
0         0%     0         0%     0         0%     66        0%     121       0%      
free_stateid     getdevicelist    bind_conn_to_ses destroy_clientid seek              
41        0%     0         0%     0         0%     0         0%     0         0%      
allocate         deallocate       layoutstats      clone             
0         0%     0         0%     0         0%     0         0%      
[/FONT]
```

And here are the mount options:
```

[FONT=monospace][COLOR=#ff5454]**nfs**[/COLOR][COLOR=#000000]d on /proc/fs/[/COLOR][COLOR=#ff5454]**nfs**[/COLOR][COLOR=#000000]d type [/COLOR][COLOR=#ff5454]**nfs**[/COLOR][COLOR=#000000]d (rw,relatime) [/COLOR]
/etc/auto.[COLOR=#ff5454]**nfs**[/COLOR][COLOR=#000000] on /mnt/server type autofs (rw,relatime,fd=6,pgrp=1496,timeout=300,minproto=5,maxproto=5,indirect,pipe_ino=31240) [/COLOR]
server:/mnt/dump on /mnt/server/dump type [COLOR=#ff5454]**nfs**[/COLOR][COLOR=#000000]4 (rw,relatime,vers=4.2,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientad[/COLOR]
dr=10.1.1.5,local_lock=none,addr=10.1.1.1)
[/FONT]
```

Any ideas what is going on?  It worked fine on 20.10, so I'm guessing it's either a default option changed or something having to do with the new kernel (I'm running [FONT=monospace][COLOR=#000000]5.13.0-20-generic on both boxes.)

[/COLOR]
[/FONT]

---

### Post by TheFu on 2021-11-22
I don't have any answer, just more data points for you to consider.

On my NFS clients, in the auto.nfs file, these are my settings:
```
/TV   -fstype=nfs,nconnect=[COLOR="#008000"]2[/COLOR],proto=tcp,rw,async  istar:/TV
```
I don't have 20.10 or 21.10 - those aren't LTS and are too new for my use.  The nconnect should probably be the lessor of number of CPUs on the NFSv4 server or client.  My NFSv4 server runs 18.04. I'll likely move to 20.04 in a few weeks. There aren't many dependencies holding that system back like there are with some other systems here.  Really just the backup tool I use is an issue.

```
$ mount | grep TV
/etc/auto.nfs on /TV type autofs (rw,relatime,fd=6,pgrp=21050,timeout=60,minproto=5,maxproto=5,direct,pipe_ino=639466)

```
are the resulting settings from an 18.04 client.

On a newer, 20.04, client:
```
$ mount | grep TV
/etc/auto.nfs on /TV type autofs (rw,relatime,fd=6,pgrp=863,timeout=300,minproto=5,maxproto=5,direct,pipe_ino=27561)
istar:/TV on /TV type nfs4 (rw,relatime,vers=4.2,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,nconnect=4,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.3,local_lock=none,addr=172.22.22.20)

```
The settings there are:
```
/TV   -fstype=nfs,nconnect=[COLOR="#008000"]4[/COLOR],proto=tcp,rw,async  istar:/TV
```

Are all protocols slower or just NFS?  Does iperf3 show the expected throughput between the problem systems?  Here, iperf3 shows 940Mbps for GigE to GigE connections and much faster connections for in-virtual-machine connections (typically 25Gbps).

There is 1 new setting on the NFS server ... the 'fsid=' number to help clients not become confused by different shares.  An /etc/exports example line:
```
/d/D1/ebooks/Library    nextcloud(ro,async,root_squash,fsid=[COLOR="#FF0000"]9[/COLOR])
```
The number just needs to be unique between the other lines in the exports file. There isn't any client-side setting.

---

### Post by damian7820 on 2021-12-02
In the update you changed the file system, for example from xfs to ext4. The first is multiple access and the second is not. Perhaps your problem lies not in the NFS4 protocol, but in the chosen file system format.

---

