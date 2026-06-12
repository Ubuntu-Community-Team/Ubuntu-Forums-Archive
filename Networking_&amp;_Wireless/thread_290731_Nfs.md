---
title: "Nfs"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-11-01
Hey
Im trying to connect to my friend NFS server.
But it doesnt go so well.
I have did following things

sudo  apt-get install portmap nfs-common
modprobe nfs
sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/portmap restart

mount -t nfs ip:/home/dmsn test

root@lappen:/home/dmsn/Desktop# rpcinfo -p x.x.x.x
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100011    1   udp    822  rquotad
    100011    2   udp    822  rquotad
    100011    1   tcp    825  rquotad
    100011    2   tcp    825  rquotad
    100003    2   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100021    1   udp  42031  nlockmgr
    100021    3   udp  42031  nlockmgr
    100021    4   udp  42031  nlockmgr
    100021    1   tcp  44082  nlockmgr
    100021    3   tcp  44082  nlockmgr
    100021    4   tcp  44082  nlockmgr
    100005    1   udp    832  mountd
    100005    1   tcp    835  mountd
    100005    2   udp    832  mountd
    100005    2   tcp    835  mountd
    100005    3   udp    832  mountd
    100005    3   tcp    835  mountd
root@lappen:/home/dmsn/Desktop#

EDIT: I just tested on my router/firewall linux box and it works well, but not on my ubuntu laptop.


What should i do, thanks ?

---

### Post by matthewstory on 2006-11-01
what does your friend's /etc/hosts.allow, /etc/hosts.deny files look like . . . are you allowed to connect from the machine you're on?

---

### Post by dmsn on 2006-11-02
yepp im allowed.

---

