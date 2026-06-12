---
title: "NFS completely borked in 22.04.2 / ~kernel 5.15.0-67 &amp; later?"
date: 2023-04-02
forum: Networking &amp; Wireless
---

### Post by 3vi1 on 2023-04-02
I recently updated one of my systems and discovered NFS (previously working for years, very simple/straight-forward config) didn't work at all after the kernel update to 5.15.0-69.  Testing was done using a client running the 6.2.7 mainline kernel.

The only previous kernel I currently had on the system at the time was 5.15.0-67.  I found that if I booted to that, I could map the drive from the client, but still experienced severe issues.  For instance, I could 'ls -l /nfs_share/subdirectory1' and see the contents of subdirectory1 but if I ran 'ls -l /nfs_share' it would hang.  Wireshark showed me that the server was just constantly replying with NFS4ERR_DELAY during the hang.

So for my next test, I installed the 5.15 mainline kernel.  Using that, everything works fine.  I went through all three kernels again and the NFS problems re-appeared exactly as before:  -69 won't mount, -67 mounted but hangs listing the root share, plain 5.15 worked fine.

I've checked out launchpad and I do see a multiple reporting possibly related NFS issues (failures to mount, CPU deathlocks) since even earlier 5.15 versions, but I'm surprised there aren't more people broken.  I suppose most people that would use NFS probably wouldn't have already updated and may be on older 5.4 or 5.15 kernels.

I'll see if I can find an existing launchpad item or open a new one for the bug:  I was just curious if any others here have already run into this and may already know of a bug reported upstream (testing with mainline 5.15.60 kernel shows the problem to exist there as well).

---

### Post by TheFu on 2023-04-03
My 
```
$ uname -r
5.15.0-69-generic
```
system isn't having any NFS-client issues.

It is connecting to these NFS servers:
[LIST]
[*] 5.15.0-69-generic
[*] 5.4.0-144-generic
[/LIST]
Both work well with 3-different LTS releases currently supported.

I use **autofs** to mount NFS from clients.  I also have specified the NFS fsid= in the server for almost all exports, so the clients don't get confused.  The fsid= seems to let NFSv4 more safely determine which NFS mount goes with which NFS share.  

I don't know that adding fsid= will help, but I did have an issue similar to this about 5 yrs ago.  That single change fixed it.  The "exports" manpage has a few paragraphs.

Anyway, worth a try.

$ egrep -o 'fsid=[0-9]+' /etc/exports 
```
fsid=10
fsid=1
fsid=2
fsid=3
fsid=4
fsid=5
fsid=6

```and on the other NFS server:
```
$ egrep -o 'fsid=[0-9]+' /etc/exports 
fsid=10
fsid=9

```
the fact that they overlap doesn't seem to matter, provided it is on a different server.

---

### Post by 3vi1 on 2023-04-29
Thank you for your reply.  My problem wasn't the fsid, but in researching it I realized just how much things have changed with NFS4.

My main problem is that I set up these shares 15+ years ago and really haven't had to think about them since.  While reviewing the implications of fsid, I saw that NFS4 uses a bit of a different heirarchy - with a virtual root as opposed to the way I had just been exporting the actual drive mount points with older NSF versions.

I created a virtual root and share directories under it, bound the correct directories to those exports, and am now able to mount the shares with the 6.3 kernel.

Thanks again for taking the time to respond.  I probably would have been puzzled with this for a lot longer if you had not gotten me to engage my brain and look at it from the ground up.

---

### Post by SeijiSensei on 2023-04-29
You can add "vers=3" to the list of options after "default" in /etc/fstab. That forces an NFS3 connection which might work better for you.

---

