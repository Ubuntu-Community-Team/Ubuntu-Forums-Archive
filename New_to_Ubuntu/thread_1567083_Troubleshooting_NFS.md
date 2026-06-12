---
title: "Troubleshooting NFS"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-03
As part of troubleshooting a problem with NFS (embedded board wont boot via NFS from PC/Ubuntu 10.04) I read somewhere that I should check my NFS server (running on the PC) like this:

[B]sudo mount localhost:/home/myname/Tools/nfsroot/ ~/mountdir

[/B]When doing it I get an error:
**mount.nfs: access denied by server while mounting localhost:/home/myname/Tools/nfsroot/**

Here is my **exports** file:

[B]# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check) 
/home/myname/Tools/nfsroot 192.168.0.100(rw,no_root_squash,no_subtree_check)
#[/B]

Here is what I get from rpcinfo:
[B]
mynamed@me-desktop:~$ rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  35041  status
    100024    1   tcp  45828  status
    100021    1   udp  39860  nlockmgr
    100021    3   udp  39860  nlockmgr
    100021    4   udp  39860  nlockmgr
    100021    1   tcp  48921  nlockmgr
    100021    3   tcp  48921  nlockmgr
    100021    4   tcp  48921  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  38890  mountd
    100005    1   tcp  51741  mountd
    100005    2   udp  38890  mountd
    100005    2   tcp  51741  mountd
    100005    3   udp  38890  mountd
    100005    3   tcp  51741  mountd[/B]


Where is the problem and how can I fix it?

Thanks,
donescamillo

---

### Post by jtarin on 2010-09-03
[Sound familiar?]("http://linux-nfs.org/pipermail/nfsv4/2009-January/009710.html")

---

### Post by donescamillo on 2010-09-03
Thanks for the help, I may have messed up something with the IP address, with * it works so I am starting from there

---

### Post by baddnady23 on 2010-09-03
> **donescamillo said:**
> Thanks for the help, I may have messed up something with the IP address, with * it works so I am starting from there

When setting up my NFS server, I tired for hours to get past a similar problem and it was simply a typo on my part in the /etc/exports.  Check and double check what you typed there...

---

