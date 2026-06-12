---
title: "How do I increase the storage size of /opt?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-11
Hello everyone,

Can I increase the size of /opt? I want to put a VirtualBox image in it with Windows 7, which will eventually use more than the 7.4 GB of space it presently has. Following the advice of another thread I started, I have permissions to read and write in /opt,(see screenshot below). 

Is this possible?

Thanks.

EDIT:  Oh and yes; to have the space to put other vm's in /opt also.

---

### Post by mcduck on 2010-02-11
There is no limit in /opt's size, just like there isn't any limit in any other directory's size.

Assuming you have /opt on your root partition the available space is exaxctly the same as available free space on your root partition.

(This is of course asuming you haven't yourself enabled disk quotas and limited the size. But if you had done that you'd probably also know how to change the quota)

---

### Post by mikodo on 2010-02-11
I guess I just don't understand this window, when trying to set up the /opt vm for windows 7. See below:

---

### Post by mikodo on 2010-02-11
Oh, I think I get it. My / partition would have to be big enough to accommodate this big of a file (vm set at fixed size of `40 gigs), which it is not. See screenshot of Gparted showing my / of Ext 4.

---

### Post by mikodo on 2010-02-11
> **mcduck said:**
> There is no limit in /opt's size, just like there isn't any limit in any other directory's size.

Assuming you have /opt on your root partition the available space is exaxctly the same as available free space on your root partition.

(This is of course asuming you haven't yourself enabled disk quotas and limited the size. But if you had done that you'd probably also know how to change the quota)

This is what you told me....dah

Thanks.

---

### Post by LowSky on 2010-02-11
Exactly Your root partition is too small. Plus your VM should place its file in your /home partition. Changing your settings to read/write to /opt I don't think was a bad idea. Sure its a file location for software, but VM needs space and should be under a single user's control, also Windows 7 will need _at least _16-20GB and that running it bare-boned. I would think you would want at least 40GB

---

### Post by mikodo on 2010-02-11
> **LowSky said:**
> Exactly Your root partition is too small. Plus your VM should place its file in your /home partition. Changing your settings to read/write to /opt I don't think was a bad idea. Sure its a file location for software, but VM needs space and should be under a single user's control, also Windows 7 will need _at least _16-20GB and that running it bare-boned. I would think you would want at least 40GB

So, for others have them set to no access. (Access for Others = None).

And repartition so my / Ext4 has at least ~ 50 GB in total.

Thanks.

---

### Post by durand on 2010-02-11
What are you using sda5 for? It's a pretty huge partition. Maybe you could make that a bit smaller, create a new ext4 partition just for VMs? That would probably be ideal.

---

### Post by mikodo on 2010-02-11
> **durand said:**
> What are you using sda5 for? It's a pretty huge partition. Maybe you could make that a bit smaller, create a new ext4 partition just for VMs? That would probably be ideal.

All that is on that is Hardy. When I set up the partitioning of the HD as present with  Karmic on sda 7&8), I thought I would be continuing to use Hardy as my main release, with Karmic just for fun, until the next LTS (Lucid) came out.

I found I liked Karmic so much, it has now become my main release and Hardy is pretty much not used at all. I have kept it on the HD, just in case something went wrong with me and Karmic. It is a little redundant now, with Karmic running "steady as she goes", and Lucid's release just around the corner.

I, in fact, have thought about, using most of that large partition for VM's also. Maybe I'll do that. I just got kinda stuck, on finding out how to place vm's in /opt and followed through to see how it could be done.

See ya,

Mike

EDIT:   I don't know the reason behind a smiley being substituted for an 8.

---

