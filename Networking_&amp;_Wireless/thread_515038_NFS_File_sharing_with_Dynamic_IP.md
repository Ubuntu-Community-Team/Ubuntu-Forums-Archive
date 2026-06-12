---
title: "NFS File sharing with Dynamic IP ?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by davidme on 2007-08-01
I followed this guide to make NFS working: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

What happens if I have a dynamic ip address ?

Say I have 2 laptops, I want one to share files to another via NFS.

Problem is that I have dynamic ip for both of them since they connect through a router.

So, if I write this:

/home/czar/tmp 192.168.1.1/24(rw,no_root_squash,async)

next time I will start my host laptop the ip for the host can be different, meaning I have to change it on the client.

Is there any other way to connect maybe via laptop name or MAC address or something ?

---

### Post by kidders on 2007-08-02
Hi there,

There's no reason you *have* to use IP addresses in your /etc/exports. Hostnames will do just fine, for instance. (See the man page for "exports" for details.)

The only issue with dynamic addressing has to do with the (normally only theoretical) possibility that the address of an NFS share (or a computer connected to one) could change suddenly, while a share is mounted. You should check that your DHCP server is configured in such a way as to *keep* that possibility theoretical. It's a common issue, that affects all file sharing protocols to some degree.

---

