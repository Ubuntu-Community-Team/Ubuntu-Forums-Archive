---
title: "NFS file sharing problem"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by lacosanostra on 2008-11-12
Hello,

I have a computer running Kubuntu 8.04 with the following /etc/exports file:

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/martin/Music/ *(rw,async,all_squash)
/home/martin/Pictures/ *(rw,async,all_squash)
/home/martin/Public/ *(rw)
/home/martin/Videos/ *(rw,async,all_squash)
/home/martin/Downloads/ *(rw,async,all_squash)


```

In another computer that running Kubuntu 8.10 I want to mount  the "/home/martin/Public/" directory by typing

```

root@martin-laptop:~/Desktop# sudo mount lacosanostra.local:/Public /home/martin/ServerPublic

```

and I get

```

mount.nfs: access denied by server while mounting lacosanostra.local:/Public

```

I don't have firewall and I can access that directory with samba.

Any suggestions?

Thanks a lot.

---

### Post by HermanAB on 2008-11-12
Hmmm, is the NFS server listening?
$ telnet serveraddress 2049

If not, restart it.

Cheers,

Herman

---

### Post by dougfractal on 2008-11-12
> /home/martin/Music/ *(rw,async,all_squash)
/home/martin/Pictures/ *(rw,async,all_squash)
/home/martin/Public/ *(rw)
/home/martin/Videos/ *(rw,async,all_squash)
/home/martin/Downloads/ *(rw,async,all_squash)

Trailing slashes ???
i.e.
/home/martin/Pictures *(rw,async,all_squash)

---

### Post by cariboo on 2008-11-12
Your exports file is not setup properly, you have to add in there which computers can access the shares.

this is what my /etc/exports file looks like:

```
/home/storage/Movies	192.168.1.1/24(rw,no_root_squash,async)
/home/storage/Data	192.168.1.1/24(rw,no_root_squash,async)
/home/storage/Mp3	192.168.1.1/24(rw,no_root_squash,async)
```

the **192.168.1.1/24** means that all the computers on my network can access the shares.

Make sure you have nfs-common installed on the client computers.

---

### Post by lacosanostra on 2008-11-12
> **HermanAB said:**
> Hmmm, is the NFS server listening?
$ telnet serveraddress 2049

If not, restart it.

Cheers,

Herman

```

$telnet lacosanostra.local 2049
Trying 192.168.2.102...
Connected to lacosanostra.local.

```

Thank you!

---

### Post by lacosanostra on 2008-11-12
> **cariboo907 said:**
> Your exports file is not setup properly, you have to add in there which computers can access the shares.

this is what my /etc/exports file looks like:

```
/home/storage/Movies	192.168.1.1/24(rw,no_root_squash,async)
/home/storage/Data	192.168.1.1/24(rw,no_root_squash,async)
/home/storage/Mp3	192.168.1.1/24(rw,no_root_squash,async)
```

the **192.168.1.1/24** means that all the computers on my network can access the shares.

Make sure you have nfs-common installed on the client computers.

I changed the export file to 

/home/martin/Music/ *(rw,async,all_squash)
/home/martin/Pictures/ *(rw,async,all_squash)
/home/martin/Public  192.168.2.1/24(rw)
/home/martin/Videos/ *(rw,async,all_squash)
/home/martin/Downloads/ *(rw,async,all_squash)

and nfs-common installed

# sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

but I get the same error if I try to mount /home/martin/Public

Thank you anyway!

---

### Post by bjhom on 2008-11-20
lacosanostra were you able to mount your nfs share?  I think that I am having the same problem.  I have one machine running Intrepid that when I try and mount an nfs share, gives the message
```
mount.nfs: access denied by server while mounting 192.168.1.4:/multimedia
```
While I have another machine running hardy that mounts the share just fine. 

The machine that doesn't work has nfs-common version 1:1.1.2-4ubuntu1.

If you, or anyone else, are able to figure it out, I would be very appreciative if you could share what you did.
Thanks.

---

### Post by rgeddes on 2008-11-21
Try restarting the server after making changes.  I'm not sure what changes require restarts or reloads, but a restart should make the changes take effect.

```
sudo /etc/init.d/nfs-kernel-server restart
```

---

