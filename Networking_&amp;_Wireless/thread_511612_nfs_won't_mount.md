---
title: "nfs won't mount"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by stefansjs on 2007-07-28
Please help.  I've been trying to get nfs to work between my two ubuntu computers.  I set up a private network between the two so that I could have static IPs.  My /etc/exports looks like this:

# /etc/exports: the access control list for filesystems which may be exported
                to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/testraid/backup 192.168.1.102(rw,sync)
/testraid/video 192.168.1.102(rw,sync)
/testraid/music 192.168.1.102(rw,sync)
/testraid/photo 192.168.1.102(rw,sync)



When I try to export the /etc/export i get:

  ~$ sudo exportfs -a
Password:
exportfs: No options for to NFS: suggest NFS(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "NFS:to".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: NFS has non-inet addr
exportfs: NFS has non-inet addr
exportfs: No options for to clients.: suggest clients.(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "clients.:to".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: clients. has non-inet addr
exportfs: clients. has non-inet addr
exportfs: No options for to See: suggest See(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "See:to".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: See has non-inet addr
exportfs: See has non-inet addr
exportfs: /etc/exports:1: syntax error: bad option list
  ~$ nano /etc/exports 

I'm assuming that these errors somehow indicate what i'm doing wrong, but i don't understand them, and google didn't help me too much.  I'm pretty sure the export is the problem because when i try to mount from the client computer i get:

   ~$ sudo mount -a
mount to NFS server '192.168.1.101' failed.
mount to NFS server '192.168.1.101' failed.
mount to NFS server '192.168.1.101' failed.
mount to NFS server '192.168.1.101' failed.
   ~$

---

### Post by noob12 on 2007-07-28
What you've done is inadvertently removed a "#" from the beginning of line 2 of the file.
The significant errors are from trying to parse that line.

Replace it and retry your exportfs.

Then do a **exportfs** with no arguments to list the exports.

---

### Post by stefansjs on 2007-07-29
Well thank you for pointing out my stupidity on that one.  That definately helped.  However, I'm now having different trouble.  When I export the file, it still gives me errors, and the client still won't mount.  I'm now getting:

~$ sudo exportfs -a
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.102:/testraid/backup".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.102:/testraid/video".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [5]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.102:/testraid/music".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [6]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.102:/testraid/photo".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0


And on the client computer I get:

~$ sudo mount -a
mount: RPC: Timed out
mount: RPC: Timed out
mount: RPC: Timed out
mount: RPC: Timed out

The errors in the exportfs don't seem to be very serious, but I don't really understand nfs, so I don't really know why it would mount on the client.
thanks

---

### Post by noob12 on 2007-07-30
The subtree_check messages are warnings.  It is taking the default (subtree_check) and warning you that in a a future version you will need to explicitly set it or turn it off.  You can look that up in **man 5 exports**.

The client errors now different.  They are probably due to not being able to reach services on either the server or the client.   Make sure you are not stopping the traffic with firewall rules on either side.  

Check that at least these services are up on the server:
> 
ps -ef | egrep '(portmap|nfsd|mountd)'

on the server.

On the client 
> 
ps -ef | grep statd


If you're not seeing these, you can manually restart the nfs stuff, but it may be easier just to reboot the hosts.

---

### Post by stefansjs on 2007-08-01
Well, it looks like everything should be working, but I can't figure it out.

The server:
~$ ps -ef | egrep '(portmap|nfsd|mountd)'
daemon    7611     1  0 16:27 ?        00:00:00 /sbin/portmap
root      7647     7  0 16:29 ?        00:00:00 [nfsd4]
root      7648     1  0 16:29 ?        00:00:00 [nfsd]
root      7649     1  0 16:29 ?        00:00:00 [nfsd]
root      7650     1  0 16:29 ?        00:00:00 [nfsd]
root      7651     1  0 16:29 ?        00:00:00 [nfsd]
root      7652     1  0 16:29 ?        00:00:00 [nfsd]
root      7653     1  0 16:29 ?        00:00:00 [nfsd]
root      7654     1  0 16:29 ?        00:00:00 [nfsd]
root      7655     1  0 16:29 ?        00:00:00 [nfsd]
root      7659     1  0 16:29 ?        00:00:00 /usr/sbin/rpc.mountd
ssulliva  7741  7528  0 17:05 pts/1    00:00:00 grep -E (portmap|nfsd|mountd)
~$ 

The client:
~$ ps -ef | grep statd
statd    19846     1  0 Jul31 ?        00:00:00 /sbin/rpc.statd
ssulliva 25020 24913  0 17:06 pts/0    00:00:00 grep statd
~$ 

also, every time i reset the nfs-kernel-server dmesg says this:

[150547.212978] nfsd: last server has exited
[150547.212986] nfsd: unexporting all filesystems
[150547.213472] RPC: failed to contact portmap (errno -5).
[150548.312485] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[150548.312528] NFSD: starting 90-second grace period

thanks

---

### Post by noob12 on 2007-08-01
Did you try rebooting the server?  The nfs services and their dependencies are actually spread across a number of /etc/init.d scripts, so rebooting may be easiest.  The portmap service doesn't seem to be running right.

If you're running a firewall make sure traffic to the NFS ports 111 and 2049 are open.  Note that NFS may use either/both UDP and TCP.

---

