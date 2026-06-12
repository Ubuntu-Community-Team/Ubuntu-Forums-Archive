---
title: "NFS strange behavior"
date: 2022-05-27
forum: Networking &amp; Wireless
---

### Post by zkab on 2022-05-27
I have Synology NAS as my LAN data-storage.
Both Windows and Ubuntu users access NAS.
Windows users access NAS via SMB and Ubuntu users via NFS ... it works OK.

After a NAS system upgrade that went without any issues ... Windows can asscess NAS as before and NAS portal looks just normal.
But on the Ubuntu side I can't access the NAS.
I had NAS set up as NFS share as follows:

forsete@balder:~$ cat /etc/auto.nfs
FARBAUTE-NASSE  -fstype=nfs4,rw   nasse:/volume1/FARBAUTE-NASSE
Anne-NAS        -fstype=nfs4,rw   nasse:/volume1/Anne-NAS

But the NFS share look strange:

forsete@balder:~$ ls -la /nfs
d---------  1 root root   20 feb 28 17:07 Anne-NAS
d---------  1 root root  194 feb 28 13:17 FARBAUTE-NASSE

It shows that I don't have any permission at all to the shares (d---------).
Since Windows access & NAS portal looks OK I guess this is not a Synology problem but an Ubuntu problem.
All of a sudden I can't access my data from Ubuntu (22.04 LTS) after an upgrade.

---

### Post by TheFu on 2022-05-27
Some cheap NAS devices don't support NFS v4.2 and there's an issue in 22.04 that it doesn't fall back or the Synology doesn't request a fallback to NFS v4.0.  Adding vers=4.0 as a mount options has helped others.  There's another post in these forums about this and the posters said that fixed the issue. I don't remember if it is ver= or vers=, sorry.

My autofs options are:
```
-fstype=nfs,nconnect=2,proto=tcp,rw,async  romulus:/raid/media/VMs
```
which results in this mount:
```
$ df -Th /VMs
Filesystem              Type  Size  Used Avail Use% Mounted on
romulus:/raid/media/VMs nfs4  1.8T  1.7T  8.5G 100% /VMs
```

I don't have a Synology. My NFS servers are all LTS Ubuntu Server releases.

---

### Post by zkab on 2022-05-28
Thanks ... I will check with Synology if they are aware of the problem before downgrading NFS

---

### Post by TheFu on 2022-05-28
Downgrading?  The mount option is just ensuring that the client mounts using the version of NFS supported by the device.

Like I already wrote, there's another thread here specific to 22.04 with the link to the solution. The 22.04 release notes has something about NFS in it too, but I don't recall the issue now. I've only tested it with 22.04 as an NFS client and didn't have issues connecting to other Ubuntu NFS.

Of course, we don't know if this version difference is actually the issue you are experiencing.  Try it. See if it works. It may not. Then there are other steps to be taken.

---

### Post by zkab on 2022-05-29
I have in /etc/fstab:
```
nasse:/volume1/FARBAUTE-NASSE /nfs/FARBAUTE-NASSE       nfs rw,vers=4.0  0 0
```
After 'sudo mount -a' I get:
```
forsete@balder:~$ mount | grep -i farbaute
nasse:/volume1/FARBAUTE-NASSE on /nfs/FARBAUTE-NASSE type nfs4 (rw,relatime,vers=4.1,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.1.16,local_lock=none,addr=192.168.1.13)

```
I don't get vers=4.0 but vers=4.1
Why?

---

### Post by TheFu on 2022-05-29
I'm less concerned with why and more concerned whether this worked or not.  Does it?

---

### Post by zkab on 2022-05-29
No ... it did not work.
Synology (BSD) have different user&group ID:s

owner group
1026 users
1030 users

but Ubuntu users have the usual owner&group ... 1000&1000, 1001&1001
That's why I can't get permission to access  my NAS from Ubuntu ... and I don't know how this could be solved.

---

### Post by TheFu on 2022-05-29
The Synology documentation is your best bet to solve this.  A uid needs to match on both sides.  Google found these: 
[https://kb.synology.com/en-ph/DSM/help/DSM/AdminCenter/file_share_privilege_nfs?version=6](https://kb.synology.com/en-ph/DSM/help/DSM/AdminCenter/file_share_privilege_nfs?version=6)
[https://superuser.com/questions/860553/user-id-mapping-with-nfs-on-synology-nas](https://superuser.com/questions/860553/user-id-mapping-with-nfs-on-synology-nas)

The gid on the client doesn't need to be the primary gid, any other gid of which the uid is a member (within the first 20 groups - there's a long-known NFS bug when too many groups exist) can be used.  In ubuntu, the 'users' group isn't standard like it is with other Unix systems.  You could create a group called 'users' and ensure the gid is 1030 on the client.

If it were me, I'd ask how to solve this in the synology forums. It can't be uncommon.  Last time I checked, Synology was using Linux, not BSD. [https://techguidecentral.com/is-synologys-software-built-on-linux-answers-and-more/](https://techguidecentral.com/is-synologys-software-built-on-linux-answers-and-more/)

---

### Post by zkab on 2022-05-29
It seems that the problem is solved.
I ssh-login to NAS and made following changes:

1) sudo chown 1000:users 'shared folder'
2) sudo chown -R 1000:users 'shared folder'/
3) sudo chmod 775 'shared folder'
4) sudo chmod -R 775 'shared folder'/

Now user & owner ID match in NAS & Ubuntu ...

---

### Post by TheFu on 2022-05-29
Glad you figured it out.

Commands 1 and 2 above are the same.  If it were me, I would have used, 
$ sudo chown -R 1000:1000 'shared folder'
and been done on the Synology.  Then used chmod from the client machine as desired.
Same for commands 3 and 4. 4 does what 3 does, so 3 was unnecessary.

Please mark this thread as **SOLVED** using the _Thread Tools_ button to help the community.

---

### Post by zkab on 2022-05-30
Thanks for your support!

---

