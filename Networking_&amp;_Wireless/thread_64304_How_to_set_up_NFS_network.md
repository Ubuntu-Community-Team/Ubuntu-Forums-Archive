---
title: "How to set up NFS network?"
date: 2005-09-10
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-09-10
I've been fighting it for days...

Using Wiki and some other threads I try to set up a simple NFS network between my laptop and desktop, both running Ubuntu (desktop as a dual boot with Windows).

The idea is to set up NFS for the times when desktop is booted into Ubuntu and SMB when it is in Windows. Then to use autofs so the laptop mounts automatically network drives. Currently SMB works, but I cannot get NFS working... i guess I can use SMB in both cases though I'd like to make this NFS thing work anyway.

So basically the setup is as follows:

desktop is called desktop with IP address 10.0.0.11
laptop (called neclaptop) has to IP addresses: one when it wired (10.0.0.3) and another when it wireless (10.0.0.13).

Currently I want to set up desktop as a server and laptop as a client.

What I have done:

**Desktop**
add the following lines in the files:
/etc/host
```
10.0.0.3  neclaptop
10.0.0.13
``` 
/etc/exports
```
/home 10.0.0.3(rw)
``` 
or I also tried
```
/home neclaptop(rw)
```
/etc/hosts.allow
```
portmap mountd nfsd statd lockd : 10.0.0.13 10.0.0.11 10.0.0.3
portmap : 10.0.0.13 10.0.0.3
portmap ypserv ypbind : 10.0.0.13 10.0.0.3
``` 

**Laptop**
/etc/fstab
10.0.0.11:home    /mnt/thehill nfs rw,hard,intr 0 0

The username and password are identical on desktop and laptop.

but when I try 
```
$ sudo mount -a
mount: 10.0.0.11:home failed, reason given by server: Permission denied
``` 


I guess I am doing something wrong, but I cannot figure out what it is exactly.

Can anyone help me with it?

---

### Post by foxy123 on 2005-09-10
I have commented line in hosts file and now can mount nfs shares...

However, when I try to copy a big file from one PC to another (6Mb) it takes ages. Small file are copied fine... Why is that?

---

