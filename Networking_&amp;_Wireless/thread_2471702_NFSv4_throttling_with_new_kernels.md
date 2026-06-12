---
title: "NFSv4 throttling with new kernels"
date: 2022-02-07
forum: Networking &amp; Wireless
---

### Post by andy152 on 2022-02-07
Hi,


  I am experiencing an issue with NFSv4 performance when running on Ubuntu 20.04 LTS, I have tested with kernels ranging from 5.4 to 5.16 and all show the same issue. The environment (tested with multiple different server models, switches and network cards all showing the same problem) is an NFS server with a 10Gbit Ethernet card connected to a single switch with multiple NFS client machines (both server and clients are running Ubuntu 20.04) all connected with 1Gbit Ethernet interfaces. The issue I see is that if you set multiple clients to copy the same single large file (5GB) that the I/O maxes out at just below 1Gbit/sec. I have tested using DD as well as a regular file copy and tar to /deb/null. I have tried this with multiple combinations of mount options, including the available subversions of NFS 4, with no kernel tuning, with some network/NFS related kernel tuning and also with default TCP cubic congestion algorithm and also new bbr algorithm, none of which makes any difference. What does make a difference is forcing NFSv3, then performance is as expected and can reach near 10Gbit/sec speeds. What also works as expected is NFSv4 on Ubuntu 16.04 LTS (with 4.15 kernel). I believe the issue is the kernel version of the client machines, as I believe the issue also exists with Ubuntu 16.04 server if the clients run a newer kernel (5.10).

The fact that the speed just reaches 1Gbit/sec and also the fact that NFSv3 works as expected makes me think that perhaps it is some network congestion control gone wrong, like all the clients throttle back to not go over their link speeds. But obviously I'm just guessing.
I have searched for similar issues being reported and have not found anything, at least nothing that helps.


So if this is a good place to raise the issue, I wonder if anyone can assist in debugging this to either find what potentially I might be doing wrong or gather the relevant information if in fact this is some type of bug. I do not have notes of all the mount options and kernel tuning I have tested unfortunately, but I am happy to redo the testing and provide full info if anyone has anything specific they think I should test. Or any other suggestions or observations would be welcome,


thanks in advance, Andy.

---

### Post by TheFu on 2022-02-07
If the NFS server isn't connected to a 10Gbps switch port, seems like that would be where the bottleneck lies or did I misread the setup?

Or if the files are stored on spinning rust (HDDs), then there is the 125MBps normal top speed for getting data off.

Which mount options are being used? My auto.nfs uses something like this:
```
/d/D1 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D1
```
The nconnect option is new in NFSv4.1+. Think it made it into the 5.x kernels around 2020. Don't quote me.

Could the NIC drivers be getting in the way?  Are they single threaded or CPU-bound (realtek)?  Broadcom and Intel seem to make better drivers, though some of the Intel 2.5Gbps drivers seem to have huge issues still - 2 yrs after release. Intel denies the issue.

I don't have any 10Gbps equipment, so besides throwing out monkey ideas, I probably cannot help. I would test on my systems, but they are busy doing some file storage that can't run short of I/O cycles, so I'm unwilling until tomorrow AM.

---

### Post by andy152 on 2022-02-08
Hi,


  thanks for the reply. The NFS server is connected with a 10Gbit Ethernet card to a 10Gbit port, all clients are connected at 1Gbit. This has been tested with multiple serves, cards and switches of different brands all show the same problem with Ubuntu 20.04 and NFS4 but do not show the problem with NFS3 or with NFS4 and Ubuntu 16.04 (in the later two cases speeds close to 10Gbit/sec are achieved), in no cases do I see single threads maxing out CPU and given that I can achieve close to 10Gbit/sec with certain software configurations I do not think I can blame the drivers, and also give I see the problem with different 10Gbit cards the drivers of all the cards cannot be the problem. I have tried many combinations of mount options and didn't find any made any difference, with the exception of mounting as NFSv3.
The files are stored on disk, but are cached into memory, as I say with NFSv3 I get 10Gbit/sec without problems, the difference is night and day,


thanks, Andy.

---

### Post by TheFu on 2022-02-08
Perhaps if you shared the different mount options AND the actual tests with timing, then someone else would be able to help?

"difference is night and day" doesn't really provide facts. What are the exact differences?

I don't have any unsupported 16.04 systems left, so cannot test that either. The kernel version and NFS module will matter more than the userland tools, right?

And we are already certain that other protocols aren't impacted? You do see full speed using rsync, http, sftp, and other file transfer protocols? Yes?

Update:
I setup some tests here with a Samsung 970 SSD after all my HDDs were unable to come close with local DAS access to fill a GigE network. The SSD didn't have any issues flooding the network with my fio tests.

Local access:   ```
WRITE: bw=2367MiB/s ([COLOR="#008000"]2482MB/s[/COLOR]), 148MiB/s-149MiB/s (155MB/s-156MB/s), io=140GiB (150GB), run=60079-60408msec
```
Over NFSv4.2:  ```
WRITE: bw=119MiB/s ([COLOR="#FF0000"]124MB/s[/COLOR]), 4551KiB/s-16.5MiB/s (4661kB/s-17.3MB/s), io=8103MiB (8496MB), run=62284-68326msec
```

Clearly the network is the limiting factor for my tests.

The nfs server is running 5.11.20-051120-generic kernel.
The nfs client is running 5.4.0-97-generic.

The file system is setup as 
```
NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9492;&#9472;vg00-home                          25G lvm  ext4        home       /d/test

$ df -Th .
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-home ext4   25G   45M   24G   1% /d/test
```

And on the client-side:
```
$ dft  .
Filesystem     Type  Size  Used Avail Use% Mounted on
istar:/d/test  nfs4   25G   44M   24G   1% /d/test
```

The mount details are:
```
istar:/d/test on /d/test type nfs4 (rw,relatime,vers=4.2,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,nconnect=2,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.6,local_lock=none,addr=172.22.22.20)

``` Most are auto-negotiated.

Without a 10Gbps network, there's no much more I can do.

---

### Post by andy152 on 2022-02-09
> **TheFu said:**
> Perhaps if you shared the different mount options AND the actual tests with timing, then someone else would be able to help?

"difference is night and day" doesn't really provide facts. What are the exact differences?


Yeah, I did mention I do not record full details of all tests unfortunately. I tried a wide selection of mount options, I did not record them but as I said if there is anything specific someone thinks I should test I will redo the test and provide full details. To give one example, I have tested with these options:

```
rw,relatime,vers=4.2,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.21.83,local_lock=none,addr=192.168.2.1
```

Regarding night and day, I have explained in both my previous posts in the thread the differences, on the one hand with old kernels or with forcing NFSv3 with newer kernels I get near 10Gbit/sec speeds (as viewed from iftop and which can also be clearly seen by the time to completion for copying the 5Gb file) over an extended time ie minutes (which obviously requires 10+ clients reading simultaneously), with newer kernels and NFSv4 I get 1GBit/sec speeds.

The issue I would think is impossible to replicate where both server and clients are connected via 1Gbit Ethernet, as I have no issue reaching 1Gbit/sec speeds.

Also, just to reinforce that this does not appear to be hardware related, this problem exists when testing with an HP DL380 G10 with Mellanox 10Gbit Ethernet connected to Cisco switch, and also on a Dell R430 with Broadcom 10Gbit Ethernet connected to a Netgear switch (just to name two of several configurations that have been tested).

Given I have shown the issue on multiple different systems, would it be appropriate to open a bug if no one can suggest a reason why this might be happening? I appreciate I will have to provide full details to open a bug, mount options etc.

thanks, Andy.

---

### Post by TheFu on 2022-02-09
Definitely open a bug. I'd use apport-bug to do that.
I would simplify the mount options. Don't specify anything that isn't required to get a connection. The rsize and wsize autonegotiate and have for over a decade.

---

### Post by andy152 on 2022-02-14
Ok, thanks for the replies. The options I posted were in fact from the mount command, not options I was specifying, ie rsize and wsize. I have opened a bug so now waiting to see what the response is....

---

### Post by andy152 on 2022-02-15
In case it is of interest to anyone, I worked out the cause of the problem. In my test environment the clients are all clones with the same hostname, and in my production environment the clients all share the same NFS root, so again all have the same hostname. NFSv4 is using the hostname to identify unique clients (I don't know the detail of what it does tbh), at least in recent kernel versions. To solve the problem you can either assign a random hostname to each client, or set a random value to nfs4_unique_id, ie:

cat /proc/sys/kernel/random/uuid | tr -d  '\n' > /sys/module/nfs/parameters/nfs4_unique_id


I have tested both of these methods and both return NFSv4 performance to expected levels (it can max out 1Gbit on the client side and 10Gbit on the server side).

---

### Post by TheFu on 2022-02-15
There is an 'fsid' export parameter to help NFSv4 keep the exports separate. I don't know when it is necessary or how it gets used, but whenever I've had problems mounting storage, adding an fsid= option with either a unique number or UUID has helped. This goes into the /etc/exports. The manpage has more about it. Just be sure NOT to use fsid=0, unless that is specifically needed for the situation.

No way would anyone else every use/assume that hostnames were all the same.  I've never seen that in 30 yrs. Seems like really bad network architecture.

---

