---
title: "I just want to map a drive!"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by jeff_scott2 on 2013-09-24
I have a Qnap server and I'm now setting up a Ubuntu server to offload some applications from the Qnap.  However I still want the new server to store files on the QNAP.

I've never setup a linux server before; all my experience is just messing around with the QNAP; installing applications and stuff.

I don't know a whole lot about this but I gather that I can mount an NFS share to something like /mnt/qnap to be able to have my programs write files to the Qnap's NFS shares.

I figured out the command should go something like this:
[B]sudo mount -t nfs 192.168.0.2:/Public /mnt/qnap
[/B]
that command gives me this error:
**mount: wrong fs type, bad option, bad superblock on 192.168.0.2:/Public,**
**       missing codepage or helper program, or other error**
**       (for several filesystems (e.g. nfs, cifs) you might**
**       need a /sbin/mount.<type> helper program)**
**       In some cases useful info is found in syslog - try**
**       dmesg | tail  or so**

So I google'd that and found some info about installing some packages that I might be missing; which was running this command:
[B]sudo apt-get install nfs-kernel-server nfs-common rpcbind

[/B]After running that command and trying the mount command again Linux comes back with:
**mount.nfs: Connection timed out**

I'm stuck now because I don't get any error so I'm not sure how to proceed!

Please help, I want to love this Ubuntu server so much!

---

### Post by spacesamurai2 on 2013-09-25
A couple of issues could be at hand here. Just for starters

1) Is 192.168.0.2 accessable from your client (able to ping it yadda yadda).

2) Is the port open?

3) Does the server side log show any info during the attempt?

---

