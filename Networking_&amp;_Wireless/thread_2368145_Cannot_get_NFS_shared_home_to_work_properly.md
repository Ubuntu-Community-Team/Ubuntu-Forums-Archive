---
title: "Cannot get NFS shared /home to work properly"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by totla on 2017-08-07
Hi, im trying to setup a system, where all clients are able to use same NFS shared /home directories, but having some difficulties, cannot get it to work properly.

So i have a NAS and i already setup a NFS shared folder there called /client_homes.

I have tried few things based on info i fould in online guides, but none of them gave me the exact thing i was looking for, so im left with questions.

Do i need to mount the nfs_shared/home folder somewhere else other than /home of client? and if i do, how do i tell the OS to setup new useraccount folders/files to that new /home mount points, be it /mnt/home for example?
Do i need to create /home/<username> manually on NFS shared folder on NAS then proceed creating use with  useradd -command?

Everywhere i look, people say "this is common practise (shared homes), but no guides on how to actually do this properly :(

---

### Post by totla on 2017-08-08
Ok, i think i got this working now, everything atleast seem ok.

Please, let me know if you see anything wrong here.

First i created a NFS shared folder on our NAS, called /server_homes
Then i continued to install common-nfs and autofs on our servers

Next i modified/created following files/lines:

auto.master:
```
/home /etc/auto.home --timout=60
```

auto.home:
```
* -fstype=nfs,rw,nosuid,soft,fsid=0 nas_address:/server_homes/&
```

Then i created the folders in NAS/server_homes for our users;
/server_homes/user1
/server_homes/user2

Then i created users1 and 2 on the servers using adduser.
I created the users in the same order on all servers so all UID's and GUID's match.
Next i copied /etc/skel for each user

And for last i rebooted all servers and created some testfiles on each user. So now all users see their own /homes on each server and testfiles created and checking from NAS the permissions are set to the UID's and GUID's and they match also.

These servers are only going to have 5-7 users total so managing UID's manually is not hard, so i decided not to use LAPD for this.

Please, let me know if you see anything wrong i might have done, or if i missed something.

Thank you!

---

### Post by hhtmp88 on 2017-08-08
The following may help:
[https://www.ryananddebi.com/2013/01/15/linuxmint-or-ubuntu-how-to-automount-synology-shares](https://www.ryananddebi.com/2013/01/15/linuxmint-or-ubuntu-how-to-automount-synology-shares)

---

### Post by totla on 2017-08-08
Above tutorial is for permanent mount, im using autofs :(

---

