---
title: "nfs does not work in 10.04"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by cwmoser on 2010-06-25
I had NFS working in 9.04.  With 10.04, I cannot get it to work.

I have an 8.04 based PC named klaatu-3 that has data the that I want to access with my new 10.04 PC named klaatu-2.

I issue:

klaatu-2: **sudo   mount -t nfs klaatu-3:/PUBLIC   /media/PUBLIC**

klaatu-2: **sudo mount -t nfs klaatu-3/PUBLIC  /media/PUBLIC**mount.nfs: No such device

It worked before.  Both the source folder and the mount point exits.

Anyone getting nfs to work in 10.04?

Carl

---

### Post by dca on 2010-06-25
You can run-down what you did w/ your 10.04 install w/ this how-to?

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
 
...maybe something missed?

---

### Post by bodhi.zazen on 2010-06-25
Did you install nfs-common and portmap on the client ? Did you start both services on the client ?

Did you configure a firewall ?

Add the -v option to the mount.

mount -t nfs -v .....

the -v option may give us more details.

---

### Post by cwmoser on 2010-06-25
I note this when I try to restart **nfs-kernel-server**:
[FONT="Courier New"][SIZE="2"]
$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
FATAL: Could not load /lib/modules/2.6.32-22-generic/modules.dep: No such file or directory
 * Not starting NFS kernel daemon: no support in current kernel.[/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-06-25
I would file a bug report on Launchpad for that one. Otherwise it appears you need to boot an older kernel.

I can not understand what you are doing from your post, I thought Ubuntu 8.04 was the nfs server, and if that is so, why are you running the nfs server kernel on the client ?

---

### Post by lkraemer on 2010-06-25
[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)

I agree with bodhi.zazen.  Your post states that an 8.04 based PC named klaatu-3 has data (Server) to access.  You must export the directory.

The general syntax for the line in /etc/fstab  file is as follows:

example.hostname.com:/ubuntu /local/ubuntu nfs size=8192,wsize=8192,timeo=14,intr





NFS Client Configuration = 10.04

Use the mount command to mount a shared NFS directory from another machine, by typing a command line similar to the following at a terminal prompt:

CLIENT Required Software Install:
For Ubuntu you will need to install these packages to mount NFS shares: 
```
 
sudo apt-get install nfs-common portmap

``` 
When configuring portmap do =not= bind loopback. If you do you can either edit
/etc/default/portmap by hand or run: 
```

sudo dpkg-reconfigure portmap 
sudo /etc/init.d/portmap restart 

``` 

CREATE DIRECTORY to MOUNT NFS Shares on CLIENT:
```

cd /
cd /mnt
sudo mkdir freenas
ls -alt

```

MOUNT your NFS shares:
```

sudo mount Your_IP_Address:/path/to/share /path/on/client
sudo mount 192.168.1.250:/mnt/mysata /mnt/freenas
sudo mount server.mydomain.com:/files to /files
sudo mount FreeNAS:/mnt/Share /mnt/freenas 

```

I have used this command with FreeNAS and it does work:
sudo mount 192.168.1.250:/mnt/mysata /mnt/freenas

You may have to restart the services to see the mount: 
```
 
sudo /etc/init.d/portmap restart 
sudo /etc/init.d/nfs-common restart 

``` 
If you have a firewall you need to make sure ports 32771, 111 and 2049 are open. 

to umount do:
```

sudo umount /mnt/freenas

```

lk

---

