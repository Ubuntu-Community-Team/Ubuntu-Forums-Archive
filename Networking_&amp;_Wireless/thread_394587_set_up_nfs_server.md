---
title: "set up nfs server"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by davidcollins001 on 2007-03-27
Hi,

I don't know if this is the correct place for this post or not. If not I would appreciate if you could point me in the right direction.

I have been trying to network boot a laptop that I have, it doesn't have a cd and won't boot from usb. I have managed to boot using an internet install but that took about 16 hours so I am reluctant to do that again. I would also like to learn more about using nfs. I am using ubuntu live for powerpc on my mac. I have an nfs capable kernel with all the nfs components static and not as modules.

Anyway, I have gotten the whole dhcp, tftp, pxe thing setup correctly, I can boot the kernel and get through that process without any problems. I have installed portmap, nfs-kernel-server, and nfs-common using apt-get.

I am getting the following error when I try to boot the client:
```

Root-NFS: Unable to get nfsd port number from server
mount: server 192.168.0.2 not responding, timed out
Root-NFS server returned error -5 while mounting /tftpboot
VFS: Unable to mount root fs via NFS, trying floppy

```

It appears to be the portmapper is not giving the booted client a port number to find the nfs server on. I have been googling like mad over the last couple of days but I can't find the solution to this error. There are a lot of posts suggesting check portmapper is running which is the first thing I did (rpcinfo -p). I tried to stop and start, and also restart from /etc/init.d/portmap, which gave me the "ok" running message. I started this first then the nfs-kernel-server and nfs-common as was suggested.

I ran exportfs -arv which told me which directory was exported, however when I looked in /proc/fs/nfs/exports the file was empty.

I tried to mount the nfs directory locally and I got a permission denied message, so checked everything that the troubleshooting in tldp suggests, but none helps. Curiously when I try to mount a folder that doesn't exist I get a "No such file or directory" error so it must be making some sort of connection?


hosts.allow and hosts.deny are both empty.

cat /etc/export
```

/tftpboot/ 192.168.0.0/24(rw,no_root_squash,sync)
/tftpboot *(ro,root_squash,sync)
/tftpboot 127.0.0.0/255.255.0.0(ro,root_squash,sync

```

$ rpcinfo -p
```

   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32784  nlockmgr
    100021    3   udp  32784  nlockmgr
    100021    4   udp  32784  nlockmgr
    100021    1   tcp  39141  nlockmgr
    100021    3   tcp  39141  nlockmgr
    100021    4   tcp  39141  nlockmgr
    100005    1   udp    978  mountd
    100005    1   tcp    981  mountd
    100005    2   udp    978  mountd
    100005    2   tcp    981  mountd
    100005    3   udp    978  mountd
    100005    3   tcp    981  mountd
    100024    1   udp  32785  status
    100024    1   tcp  58018  status

```

I have just had a look in my /var/log/messages and /var/log/syslog files, I noticed that it says that it authenticated mount request, but also says that RPC failed to contact portmap - I'm totally lost!

/var/log/messages:
```

ubuntu@ubuntu:/tftpboot$ tail -n 15 /var/log/messages 
Mar 26 19:47:11 ubuntu kernel: [110752.546789] nfsd: last server has exited
Mar 26 19:47:11 ubuntu kernel: [110752.546803] nfsd: unexporting all filesystems
Mar 26 19:47:11 ubuntu kernel: [110752.547480] RPC: failed to contact portmap (errno -5).
Mar 26 19:47:12 ubuntu kernel: [110754.007247] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 26 19:47:12 ubuntu kernel: [110754.007868] NFSD: starting 90-second grace period

```


/var/log/syslog
```

Mar 26 19:47:11 ubuntu mountd[13397]: Caught signal 15, un-registering and exiting.
Mar 26 19:47:11 ubuntu kernel: [110752.546789] nfsd: last server has exited
Mar 26 19:47:11 ubuntu kernel: [110752.546803] nfsd: unexporting all filesystems
Mar 26 19:47:11 ubuntu kernel: [110752.547480] RPC: failed to contact portmap (errno -5).
Mar 26 19:47:12 ubuntu kernel: [110754.007247] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 26 19:47:12 ubuntu kernel: [110754.007868] NFSD: starting 90-second grace period
Mar 26 19:47:18 ubuntu rpc.statd[13432]: Caught signal 15, un-registering and exiting.
Mar 26 19:47:19 ubuntu rpc.statd[13630]: Version 1.0.9 Starting
Mar 26 19:47:41 ubuntu mountd[13596]: authenticated mount request from 192.168.0.2:671 for /home/ubuntu/tmp (/home/ubuntu/tmp)

```


Sorry for my long rambling post but I have no idea what I have done wrong or how to solve it.:confused: :( 

Thanks

---

### Post by hde on 2007-03-27
It could just be that you made a typo in your post, but it's not

/etc/export

but

/etc/exports

---

### Post by davidcollins001 on 2007-03-28
Yes, I think it is a typo since I always use the command line completion.

Does anyone have any idea what I may be missing? I have done a lot of googling and I can't find what I am missing. Setting up NFS seems very straight forward to setup -- a nfs capable client kernel, an nfs server and portmap, and an entry in /etc/exports. With everything started and the share exported. 

I guarantee that I am missing something very simple but it is beyond me what it is?

---

### Post by davidcollins001 on 2007-03-31
I am still struggling with this problem and still googling away does anyone have any advice for me? I will try anything. I have changed tack with this. Instead of trying to mount the other laptop and boot it I am trying to mount localhost.

I have been on [http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING), and the closest error that I can find is this one: [http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#SYMPTOM3](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#SYMPTOM3). My  /proc/fs/nfs/exports file is empty, which they say means I haven't exported correctly, but I have done sudo exportfs -rav which still leaves /proc/fs/nfs/exports empty.

I have used modprobe to insert nfs support into the kernel, and /proc/filesystems showed this. I am on a live version of ubuntu on powerpc, I don't know if this would cause problems? As far as I can see and from my research I have set everything up correctly.

Sorry for my posts being long rambling and desperate but I really don't know what to try next?

---

### Post by zedzed on 2007-04-06
David, Have you gotten this to work?

I'm seeing very similar results and the only thing that has shown any promise is when I place the client ip address in the NFS server's /etc/hosts file, the connection works.  It doesn't seem to matter what I do with hosts.allow or hosts.deny.  I've been using a simple exports file.  

exports:
/opt/image *(no_root_squash,async)

portmap -p is identical when ran on either the client or the server

Anyways, have you made progress?

---

### Post by dvord on 2007-04-21
Same thing here.  I've tried using the subnet, IP address of the client or the name of the client as defined in Hosts, but I cannot get by Permission denied.

Hosts.allow and .deny are empty.

My /proc/fs/nfs/exports file is also blank after exportfs -ra 

I am using two new Feisty Fawn installs to do this.

---

### Post by baristamarcel on 2007-06-17
I experienced the same problem but got things working ok by using the user-space nfs3 package (unfs3). Looks like a bug in the feisty nfs4 packages .. (?)

---

