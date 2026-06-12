---
title: "Help! Yet another &quot;mount.nfs: access denied&quot; Question"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-07-22
Gurus,

I have two hosts running Lucid 10.04. Host A is 32 bits & B is 64 bits. I need to automount (via fstab) a directory from B to A so here is what I did:

1) installed samba, nfs server and client on both hosts.
2) configured /etc/exports on HOST B: 

```
/opt    HOST_A_ip_address(rw,no_root_squash,async)
```3) on HOST_A, edited /etc/fstab to add

```
HOST_B:/opt    /mnt/<some_name>    nfs    defaults    0    0
```4) when I did ` sudo mount -a`, I get

```
$> mount.nfs: access denied by server while mounting B_HOST_B:/opt/
```5) I get the same error when I type the command line 

```
sudo mount HOST_B:/opt/ /mnt/<some_name>
```6) directory /opt on HOST_B is chmod-ed +rwx, so is  /mnt/<some_name> on HOST_A.

What am I missing? Can someone please help? 

Thanks,

Al.

---

### Post by kristo5747 on 2010-07-22
I simply forgot to reboot...:oops:

All is well now.

---

