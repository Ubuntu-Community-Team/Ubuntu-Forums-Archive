---
title: "NFS copy performance question"
date: 2019-08-15
forum: Networking &amp; Wireless
---

### Post by ab72 on 2019-08-15
I am copying from one Ubuntu machine (A) to another machine (B) by NFS mounting A's dirA on B as /mnt/A/dirA.  When logged into B, I'll execute:

cp --verbose /mnt/dirA/subdir1/*.csv /<some new location on B>/

This works as expected, but it isn't very fast.  However, if I simultaneously launch a second command from B:

cp --verbose /mnt/dirA/subdir2/*.csv /<some other new location on B>/

Then I notice that the fist copy command speeds up dramatically (by a factor of 5-10, it's obvious from watching the filenames fly by as the command progresses).  I would have suspected that the second copy command would be more likely to slow down the first one.  This behavior is very repeatable.

Why does this happen?

I'm new to setting up my own NFS mounts, so I suspect this is a sign that I haven't done it correctly.  If this is true, I'd also like to know what I need to fix.

---

### Post by TheFu on 2019-08-15
Welcome to the forums.

Perhaps if you showed the NFS server configs 
and 
the NFS client configs/mount options
and
described the disk subsystem on both sides and  how the network is setup?  How are both systems connected?

---

### Post by ab72 on 2019-08-16
Thanks TheFu.  

The client mount options (from /etc/fstab) are:

<machine A>.local:<dir on A> /mnt/A/dirA nfs ro,async,noacl,nocto,noatime,rsize=32768,wsize=32768  0  0

(I've changed the names of the machines and dirs for privacy, hopefully this isn't too much of an obstacle)

I've  tried some other mount options (without async,noacl,nocto,noatime, and  also setting rsize and wsize to 8K), but nothing has changed.

Are there other client config files you would like to see?  What files contain the NFS server configs you mention?

Regarding  the disk subsystem, the disk on machine A is a 1TB SSD formatted as  ext4.  The disk on machine B is a 512GB SSD also formatted as ext4.  

The  network is through my home router, the standard Verizon FiOS one.   Machine A is connected over WiFi to the router, and machine B is  connected via ethernet.  I'm aware that I'll get improved performance by  moving A's connection from WiFi to ethernet, and I plan to do this.   However, I have a suspicion that WiFI isn't the reason I'm seeing this  weird behavior.

Also, I initially shared the folder on machine A via instructions here: [http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/)
I know those instructions are for Samba and I'm now mounted via NFS, but thought it might be worth mentioning.

---

### Post by SeijiSensei on 2019-08-16
> wsize=327 68
Is that just a typo, or is there really a space between 327 and 68?  That would set the write size to 327 bytes which would certainly have a deleterious effect on performance.

---

### Post by ab72 on 2019-08-16
Hi SeijiSensei, yep, that's a cut&paste error.  I'll fix it above.  Thanks.

---

### Post by ab72 on 2019-08-16
Actually it is some sort of formatting error, there is no space when I try to edit the post.  I'll see if I can fix the formatting, but until I get that right, please just mentally erase the space.

---

### Post by TheFu on 2019-08-16
I've never understood the need to hide internal names/IPs.

Wifi is almost certainly the issue.  People think their wifi is better than it really is.  Forget the reported "connection", that has little to do with the actual throughput any wifi link, in a wifi-centric location, can support.  Can you turn off all other wifi devices?  Every device connected to the network impacts throughput for every other device.

Rather than "seems slow", can you gather some facts?  How large are the files? Are they larger than the available disk buffers?  At some point, the data has to be written. With using SSDs, the network is almost certainly the problem.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            15G         10G        2.8G        1.6M        **2.7G**        4.8G
Swap:          975M        972M        3.3M
```

On the NFS server, the /etc/exports file is the config.
On the NFS client, the /etc/fstab or autofs files hold the config.

A line from my exports (istar is the hostname, it is a Pentium G3258):
```
/D      lubuntu(rw,async,root_squash) romulus(rw,root_squash,async) hadar(rw,root_squash,async) posc(rw,async,root_squash) osmc(rw,async,root_squash) win7-tf-lan(rw,async,root_squash) pi3(rw,async,root_squash)
```

I use autofs, so my mounts on the client side don't translate exactly to fstab lines, but the options do:
```
/D       -fstype=nfs,hard,intr,rw,async,vers=3  istar:/D
```

I've never bothered with specifying any sizes.  The defaults have worked fine.  Don't use hard mounts over wifi.
```
$ dd bs=8M count=169 if=/dev/zero of=./TEST
169+0 records in
169+0 records out
1417674752 bytes (1.4 GB, 1.3 GiB) copied, 21.1319 s, **67.1** MB/s

```
From another machine:
```
$ dd bs=8M count=169 if=/dev/zero of=./TEST
169+0 records in
169+0 records out
1417674752 bytes (1.4 GB, 1.3 GiB) copied, 19.6812 s, **72.0** MB/s

```
These results are more about the disk buffers (ram) and network then the speed of the disks. I get 920 Mbps network speeds, so that is about 115MBps before any NFS or disk overhead.  Both clients have Intel NICs.  The NFS server is using a crap Realtek NIC.

On a local SATA SSD, 
```
$ dd bs=8M count=169 if=/dev/zero of=./TEST
169+0 records in
169+0 records out
1417674752 bytes (1.4 GB, 1.3 GiB) copied, 2.43093 s, **583** MB/s
```
and a local SATA WD-Blue disk:
```
$ dd bs=8M count=169 if=/dev/zero of=./TEST
169+0 records in
169+0 records out
1417674752 bytes (1.4 GB, 1.3 GiB) copied, 8.20136 s, **173** MB/s
```

I'm not convinced that writing a bunch of zeros to a file actually tests much.

I have strict control over name resolution and don't trust avahi because of early issues with it years ago. It appears you are using avahi.  Does changing to IP addresses help?

I do NOT use wifi here, except for phones and tablets. Every other type of device is wired.  I have too much professional experience (thousands of deployments) with wifi to use it at home.  My wifi-only laptops all use a USB3-to-GigE network adaptor.

I'm planning to change from udp to tcp for my NFS uses since my network is 100% GigE. Just need to put together a plan first.

Anyways, some facts can help.

---

### Post by ab72 on 2019-08-16
Thanks TheFu.  On the server, my /etc/exports file contains:
```
<dir on A> <machine B>(ro)
```
So on the server side I just declare the directory as read-only, everything else is left as default.
As far as filesizes go, all of the files are below 1MB, the largest is 906KB.  There are 4181 files and 3651 of them are 500KB or smaller in size.
Here is the 'free' command run on the server disk:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            15G        2.6G        358M        338M         12G         12G
Swap:            0B          0B          0B

```
and on the client disk:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            62G        4.7G         47G        229M         10G         57G
Swap:           15G          0B         15G

```

Since the only dir mounted via NFS is read-only I don't think running the 'dd' command will tell us anything, but correct me if I misunderstood.

Yes, I've been using avahi instead of IP addresses, I'll try switching to see if that helps.

Given that starting a second file copy thread speeds up the first thread, do you think it is some sort of handshake between the machines that is causing this?  Perhaps a single thread is slow enough that the handshake needs to happen every file, but the two separate threads make requests fast enough that only an initial handshake is necessary?  'Handshake' might not be the most accurate term, but hopefully my question/comment is clear.

Thanks again for the help.

---

### Post by ab72 on 2019-08-16
TheFu, I switched over to using static IP instead of avahi, but I still have the issue that the second simultaneous cp speeds up the first.

---

### Post by TheFu on 2019-08-16
You are correct, a read-only mount won't be tested by attempting to write to the NFS disk. I use read-only mounts to my nextcloud server, which I don't actually trust.

If I were copying lots of files, I'd use **rsync** so restarting didn't recopy files that already were there.  On a fresh cp, it shouldn't matter.

Try adding the **async** option to the client-side mount.
Also, see if nfs is having to retransmit a bunch (network issues?):
```
$ nfsstat
```

Tweaking the MTU for the network to 9K frames can provide a 30% performance improvement according to Dell. All the network devices need to support that change, along with the client and server. This isn't a NFS-specific change. The router would need a change to support the larger MTU.  I don't know if any wifi supports jumbo frames.

You can use **iperf3** between the client and server to test the network. Let's eliminate networking as the issue.
iperf3 -s  # run on the server
iperf3 -c {IP to server}

```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 36312 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   922 Mbits/sec    0    106 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   922 Mbits/sec    0    113 KBytes       
[  4]   2.00-3.00   sec   110 MBytes   920 Mbits/sec    0    119 KBytes   
```

If you can, create a 20MB - 1GB file and put it on the server. I'd use dd to make it.  Then copy that file to the client over NFS, but use **time** to get an accurate time. Now you have a data for a MBps calculation.  Wall clock time is close enough, but time will provide that.  Facts.  We're still trying to get actual transfer facts.

---

### Post by TheFu on 2019-08-16
> **ab72 said:**
> TheFu, I switched over to using static IP instead of avahi, but I still have the issue that the second simultaneous cp speeds up the first.

Yep.  Avahi has worked for most people the last 5 years or so.  My issues were almost a decade ago and I remember all the pain, so it gets purged from all my systems.  avahi and nano and update-notifier-common and bluez and network-manager, and about 10 other packages I never want to see on my systems, ever. ;)

---

### Post by ab72 on 2019-08-16
Here is nfsstat on the client:
```
$ nfsstat
Server rpc stats:
calls      badcalls   badfmt     badauth    badclnt
0          0          0          0          0       

Client rpc stats:
calls      retrans    authrefrsh
78862      0          78863   

Client nfs v4:
null             read             write            commit           open             
1         0%     34898    44%     0         0%     0         0%     16        0%     
open_conf        open_noat        open_dgrd        close            setattr          
0         0%     9880     12%     0         0%     9880     12%     0         0%     
fsinfo           renew            setclntid        confirm          lock             
3         0%     0         0%     0         0%     0         0%     0         0%     
lockt            locku            access           getattr          lookup           
0         0%     0         0%     9         0%     5464      6%     8640     10%     
lookup_root      remove           rename           link             symlink          
1         0%     0         0%     0         0%     0         0%     0         0%     
create           pathconf         statfs           readlink         readdir          
0         0%     2         0%     0         0%     0         0%     147       0%     
server_caps      delegreturn      getacl           setacl           fs_locations     
5         0%     9880     12%     0         0%     0         0%     0         0%     
rel_lkowner      secinfo          fsid_present     exchange_id      create_session   
0         0%     0         0%     0         0%     2         0%     1         0%     
destroy_session  sequence         get_lease_time   reclaim_comp     layoutget        
0         0%     32        0%     0         0%     1         0%     0         0%     
getdevinfo       layoutcommit     layoutreturn     secinfo_no       test_stateid     
0         0%     0         0%     0         0%     1         0%     0         0%     
free_stateid     getdevicelist    bind_conn_to_ses destroy_clientid seek             
0         0%     0         0%     0         0%     0         0%     0         0%     
allocate         deallocate       layoutstats      clone            
0         0%     0         0%     0         0%     0         0% 
```

and the server:

```
$ nfsstat
Server rpc stats:
calls      badcalls   badfmt     badauth    badclnt
78908      0          0          0          0       

Server nfs v4:
null             compound         
1         0%     78906    99%     

Server nfs v4 operations:
op0-unused       op1-unused       op2-future       access           close            
0         0%     0         0%     0         0%     9890      3%     9880      3%     
commit           create           delegpurge       delegreturn      getattr          
0         0%     0         0%     0         0%     9877      3%     33880    11%     
getfh            link             lock             lockt            locku            
8633      3%     0         0%     0         0%     0         0%     0         0%     
lookup           lookup_root      nverify          open             openattr         
8641      3%     0         0%     0         0%     9915      3%     0         0%     
open_conf        open_dgrd        putfh            putpubfh         putrootfh        
0         0%     0         0%     78830    27%     0         0%     3         0%     
read             readdir          readlink         remove           rename           
34879    12%     147       0%     0         0%     0         0%     0         0%     
renew            restorefh        savefh           secinfo          setattr          
0         0%     0         0%     0         0%     0         0%     0         0%     
setcltid         setcltidconf     verify           write            rellockowner     
0         0%     0         0%     0         0%     0         0%     0         0%     
bc_ctl           bind_conn        exchange_id      create_ses       destroy_ses      
0         0%     0         0%     3         0%     3         0%     2         0%     
free_stateid     getdirdeleg      getdevinfo       getdevlist       layoutcommit     
0         0%     0         0%     0         0%     0         0%     0         0%     
layoutget        layoutreturn     secinfononam     sequence         set_ssv          
0         0%     0         0%     1         0%     78880    27%     0         0%     
test_stateid     want_deleg       destroy_clid     reclaim_comp     allocate         
0         0%     0         0%     1         0%     2         0%     0         0%     
copy             copy_notify      deallocate       ioadvise         layouterror      
0         0%     0         0%     0         0%     0         0%     0         0%     
layoutstats      offloadcancel    offloadstatus    readplus         seek             
0         0%     0         0%     0         0%     0         0%     0         0%     
write_same       
0         0%   
```  

Note that I ran these when I wasn't actively copying.

Here is iperf3 on the client side:

```
$ iperf3 -c 192.168.1.176
Connecting to host 192.168.1.176, port 5201
[  4] local 192.168.1.180 port 45710 connected to 192.168.1.176 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  4.06 MBytes  34.0 Mbits/sec    0    209 KBytes       
[  4]   1.00-2.00   sec  5.12 MBytes  42.9 Mbits/sec    0    440 KBytes       
[  4]   2.00-3.00   sec  4.98 MBytes  41.8 Mbits/sec    0    662 KBytes       
[  4]   3.00-4.00   sec  4.38 MBytes  36.8 Mbits/sec    0    871 KBytes       
[  4]   4.00-5.00   sec  4.30 MBytes  36.1 Mbits/sec    0   1.03 MBytes       
[  4]   5.00-6.00   sec  3.91 MBytes  32.8 Mbits/sec    0   1.20 MBytes       
[  4]   6.00-7.00   sec  4.44 MBytes  37.2 Mbits/sec    0   1.35 MBytes       
[  4]   7.00-8.00   sec  3.92 MBytes  32.9 Mbits/sec    0   1.35 MBytes       
[  4]   8.00-9.00   sec  4.25 MBytes  35.7 Mbits/sec    1   1.35 MBytes       
[  4]   9.00-10.00  sec  4.42 MBytes  37.1 Mbits/sec    3   1.35 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  43.8 MBytes  36.7 Mbits/sec    4             sender
[  4]   0.00-10.00  sec  43.7 MBytes  36.7 Mbits/sec                  receiver

iperf Done.
```

and simultaneously on the server side:
```
$ iperf3 -s
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 192.168.1.180, port 45708
[  5] local 192.168.1.176 port 5201 connected to 192.168.1.180 port 45710
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-1.00   sec  3.75 MBytes  31.4 Mbits/sec                  
[  5]   1.00-2.00   sec  4.57 MBytes  38.3 Mbits/sec                  
[  5]   2.00-3.00   sec  4.57 MBytes  38.3 Mbits/sec                  
[  5]   3.00-4.00   sec  4.54 MBytes  38.1 Mbits/sec                  
[  5]   4.00-5.00   sec  4.15 MBytes  34.8 Mbits/sec                  
[  5]   5.00-6.00   sec  4.23 MBytes  35.5 Mbits/sec                  
[  5]   6.00-7.00   sec  4.11 MBytes  34.5 Mbits/sec                  
[  5]   7.00-8.00   sec  3.87 MBytes  32.4 Mbits/sec                  
[  5]   8.00-9.00   sec  4.25 MBytes  35.6 Mbits/sec                  
[  5]   9.00-10.00  sec  4.43 MBytes  37.2 Mbits/sec                  
[  5]  10.00-10.29  sec  1.27 MBytes  36.5 Mbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-10.29  sec  0.00 Bytes  0.00 bits/sec                  sender
[  5]   0.00-10.29  sec  43.7 MBytes  35.6 Mbits/sec                  receiver
```

Reading the man page for iperf3, it looks like running the client command with '-R' is actually closer to what I am doing (since I'm copying from the server to the client).

In that case, the client results look like:
```
$ iperf3 -c 192.168.1.176 -R
Connecting to host 192.168.1.176, port 5201
Reverse mode, remote host 192.168.1.176 is sending
[  4] local 192.168.1.180 port 46012 connected to 192.168.1.176 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec  11.5 MBytes  96.4 Mbits/sec                  
[  4]   1.00-2.00   sec  12.0 MBytes   100 Mbits/sec                  
[  4]   2.00-3.00   sec  11.9 MBytes  99.5 Mbits/sec                  
[  4]   3.00-4.00   sec  12.0 MBytes   101 Mbits/sec                  
[  4]   4.00-5.00   sec  11.7 MBytes  98.3 Mbits/sec                  
[  4]   5.00-6.00   sec  12.0 MBytes   101 Mbits/sec                  
[  4]   6.00-7.00   sec  12.1 MBytes   101 Mbits/sec                  
[  4]   7.00-8.00   sec  11.8 MBytes  99.2 Mbits/sec                  
[  4]   8.00-9.00   sec  11.8 MBytes  99.2 Mbits/sec                  
[  4]   9.00-10.00  sec  11.9 MBytes   100 Mbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   121 MBytes   101 Mbits/sec    0             sender
[  4]   0.00-10.00  sec   119 MBytes  99.9 Mbits/sec                  receiver

iperf Done.
```

and the server side gives:
```
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 192.168.1.180, port 46010
[  5] local 192.168.1.176 port 5201 connected to 192.168.1.180 port 46012
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  5]   0.00-1.00   sec  13.3 MBytes   111 Mbits/sec    0    390 KBytes       
[  5]   1.00-2.00   sec  11.9 MBytes  99.6 Mbits/sec    0    458 KBytes       
[  5]   2.00-3.00   sec  12.3 MBytes   103 Mbits/sec    0    486 KBytes       
[  5]   3.00-4.00   sec  12.2 MBytes   103 Mbits/sec    0    486 KBytes       
[  5]   4.00-5.00   sec  11.6 MBytes  97.0 Mbits/sec    0    513 KBytes       
[  5]   5.00-6.00   sec  11.8 MBytes  99.0 Mbits/sec    0    513 KBytes       
[  5]   6.00-7.00   sec  12.7 MBytes   107 Mbits/sec    0    513 KBytes       
[  5]   7.00-8.00   sec  11.6 MBytes  97.5 Mbits/sec    0    513 KBytes       
[  5]   8.00-9.00   sec  11.6 MBytes  97.0 Mbits/sec    0    513 KBytes       
[  5]   9.00-10.00  sec  11.7 MBytes  98.0 Mbits/sec    0    513 KBytes       
[  5]  10.00-10.02  sec  0.00 Bytes  0.00 bits/sec    0    513 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  5]   0.00-10.02  sec   121 MBytes   101 Mbits/sec    0             sender
[  5]   0.00-10.02  sec  0.00 Bytes  0.00 bits/sec                  receiver
```

I don't have any experience interpreting this output, do you see anything that indicates a problem?

Now I'll try your async and time recommendations and reply with results.

I'm not trying your MTU suggestion yet, as it sounds complicated.  Do you think it is much more likely to solve my issue than the other things we are trying?

---

### Post by ab72 on 2019-08-16
Actually the client /etc/fstab mount is already using the async option.

---

### Post by ab72 on 2019-08-16
I made two files on the server, a 20MB one (TEST) and a 1GB one (TEST_L).  Here are the time cp results:
```
$ time cp TEST ~/NVMe1/Data/

real    0m2.230s
user    0m0.005s
sys     0m0.063s
```
```
$ time cp TEST_L ~/NVMe1/Data/

real    1m31.653s
user    0m0.042s
sys     0m3.156s

```
The small file is copied at about 9MB/sec and the larger one is copied at about 11MB/sec.

---

### Post by ab72 on 2019-08-16
One other datapoint, if I run time on each of the copies when running a single thread, the 'real' values are mostly in the range of 0.100-0.300s per file.  But when I start the second simultaneous thread, the 'real' values on the first thread drop to 0.013-0.016s

---

### Post by TheFu on 2019-08-16
iperf3 says you have a 100mbps network.  That means nfs can't be any faster than that.

100/8 = .... ?  That's the theoretical max performance.  Add in 10-20% for protocol overhead ... Looks like your network is the problem, not NFS.

100 base-tx networks don't support jumbo frames.  

This is solved in my mind.

---

### Post by ab72 on 2019-08-16
This explains why copies are slow in general in this setup, I agree, and  thanks for walking me through that.  However, I still don't understand  why initiating the second copy speeds up the first one.

---

