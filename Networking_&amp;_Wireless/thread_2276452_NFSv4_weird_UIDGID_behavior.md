---
title: "NFSv4 weird UID/GID behavior"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by ancoron-luciferis on 2015-05-02
**The environment:**
[LIST]
[*]NFSv4 server: Synology DS-1813+
[LIST]
[*]Linux kernel 3.2.40 x86/64-bit 
[/LIST]
  
[*]NFSv4 client: Ubuntu 14.10
[LIST]
[*]Linux kernel 3.19.0 x86/64-bit 
[*]nfs-common version: 1.2.8-9ubuntu1.1 
[/LIST]
  
[/LIST]

**The problem:**
[LIST]
[*]after mounting NFS exports from the Synology box using type "nfs4", all files and directories are shown as owned by user and group "root", although effective permissions are applied according to the UID/GID of the respective directory/file as on the NFS-server 
[/LIST]

**An example:**

On the server I have the following directory:
```

server> ls -la /volume1/homes/ancoron/
drwxr-xr-x    2 ancoron  users         4096 Dec 11 01:39 .
dr-xr-xr-x    5 root     root          4096 Dec 11 01:39 ..
server> ls -lna /volume1/homes/ancoron/
drwxr-xr-x    2 1026     100           4096 Dec 11 01:39 .
dr-xr-xr-x    5 0        0             4096 Dec 11 01:39 ..

```

As you see, on the server I have a user-owner directory, where the user-ID is 1026.

The export for this directory is a single one for the upper "home" directory:
```

/volume1/homes  192.168.6.0/24(rw,async,no_wdelay,root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)

```

To handle the UID for the user "ancoron", I have the following idmap definition:
```

server> cat /etc/idmapd.conf
[General]
Domain=homezone.localdomain
[Mapping]
Nobody-User=guest
Nobody-Group=users
[Translation]
Method=static,nsswitch
GSS-Methods=static,synomap
[Static]
ancoron@homezone.localdomain = ancoron

```

...which - as far as I understand up to now - should tell the NFSv4 server to map any incoming "ancoron@homezone.localdomain" user to the local user "ancoron".

Now, on the Ubuntu client side I am mounting the directory like this:
```

$ sudo mount -t nfs4 -o hard,intr server:/volume1/homes/ancoron /net/server/home

```

...and a listing shows the following:
```

$ ls -la /net/server/home/
total 8
drwxr-xr-x 2 root root 4096 Dec 11 01:39 .
drwxr-xr-x 4 root root 4096 May  2 19:27 ..

```

...so what??? If it would show up as "nobody" or something with the local UID/GID equivalent of the "anonuid/-gid" NFS export setting, I would at least see that ID-mapping just doesn't work, but "root"? Weird...

And a simple test confirms that it is really not just a presentation issue:
```

$ touch /net/server/home/file
touch: cannot touch ‘/net/server/home/file’: Permission denied
$ sudo touch /net/server/home/file
touch: cannot touch ‘/net/server/home/file’: Permission denied

```

...in parallel, I have the "idmapd" running in the foreground on the server-side.
When mounting, I see the following:
```

idmapd: nfsdcb: authbuf=192.168.6.0/24 authtype=user
idmapd: Server : (user) id "0" -> name "root@homezone.localdomain"
idmapd: nfsdcb: authbuf=192.168.6.0/24 authtype=group
idmapd: Server : (group) id "0" -> name "root@homezone.localdomain"

```

...however, when executing the "touch" as a regular user on the client, I see:
```

idmapd: nfsdcb: authbuf=192.168.6.0/24 authtype=user
idmapd: Server : (user) id "1026" -> name "ancoron@homezone.localdomain"
idmapd: nfsdcb: authbuf=192.168.6.0/24 authtype=group
idmapd: Server : (group) id "100" -> name "users@homezone.localdomain"

```

...so, erh... now I'm confused! It seems to get the correct user translated but still says "permission denied"?

...but it gets a bit more weird...

On the server, I've just created a new directory with numeric UID 1000 as that is the UID of the user "ancoron" at the Ubuntu client:
```

server> ls -la /volume1/homes/ancoron/
drwxr-xr-x    3 ancoron  users         4096 May  2 20:21 .
dr-xr-xr-x    5 root     root          4096 Dec 11 01:39 ..
drwx------    2 1000     root          4096 May  2 20:21 test-dir

```

...let's see how that looks at the Ubuntu client side:
```

$ ls -la /net/server/home
total 12
drwxr-xr-x 3 root root 4096 May  2 20:21 .
drwxr-xr-x 4 root root 4096 May  2 19:27 ..
drwx------ 2 root root 4096 May  2 20:21 test-dir

```

...errr... OK, the "root" as before, but now see this:
```

$ cd /net/server/home/test-dir/
$ touch file
$ ls -la
total 8
drwx------ 2 root root 4096 May  2  2015 .
drwxr-xr-x 3 root root 4096 May  2 20:21 ..
-rw-rw-r-- 1 root root    0 May  2  2015 file
$ echo "content" > file
$ ls -la
total 12
drwx------ 2 root root 4096 May  2 20:26 .
drwxr-xr-x 3 root root 4096 May  2 20:21 ..
-rw-rw-r-- 1 root root    8 May  2  2015 file
$ cat file
content
$ rm file
$ ls -la
total 8
drwx------ 2 root root 4096 May  2 20:26 .
drwxr-xr-x 3 root root 4096 May  2 20:21 ..

```

...meanwhile, on the server, the test file looks like this:
```

server> ls -la /volume1/homes/ancoron/test-dir/
drwx------    2 1000     root          4096 May  2 20:27 .
drwxr-xr-x    3 ancoron  users         4096 May  2 20:21 ..
-rw-rw-r--    1 1000     1000             8 May  2 20:27 file

```

**Can anyone please explain to me what is going on here?**

The id mapping on the server is being created (although quite a weird mapping):
```

server> cat /proc/net/rpc/nfs4.nametoid/content
#domain type name [id]

server> cat /proc/net/rpc/nfs4.idtoname/content
#domain type id [name]
192.168.6.0 group 100 users@homezone.localdomain
192.168.6.0 group 1000 users
192.168.6.0 user 1000 guest
192.168.6.0 group 0 root@homezone.localdomain
192.168.6.0 user 1026 ancoron@homezone.localdomain

```

---

