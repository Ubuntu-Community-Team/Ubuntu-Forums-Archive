---
title: "partitioning external hard drive for ubuntu installation"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by thatdudejslate on 2010-03-16
Okay, so I'm new to Ubuntu. I'm already running Windows Vista and have all my partitions for windows set up how I want. I don't really want to mess with it, so I'm just wanting to do everything Ubuntu on my 250GB external hard drive while I adapt to the new OS. However, I want to use only the space I need for Ubuntu, and use the rest of the free space for whatever else (mostly just music and media).

Im wanting to install Ubuntu 9.10 off of the the LiveCD demo. Everything goes good until its time to set up the partitions on the external. In setup, I choose to manually select my partitions. The hard drive has been formatted, so I see about 230GB of free space. So...

I set different partitions as follows:

about 10 GB as a primary ext4 with a '/' mount at beginning
about 6 GB as a primary swap
about 20 GB as primary ext4 with '/home' mount at beginning
I leave the rest as free space.

Then when I forward to the last step, it says something like... 'can't unmount partition' or something... then gives me a location to something in the external and asks me to close all applications using it. then asks things like 'should it continue to try to unmount?' or it wants to erase all partitions or something. Either way, it will start scanning the disk.. then knock me back a couple steps to the partition setup and start all over.

I feel close, but man, I dont even know... I just want to get to know linux! :D

Any advice? Thanks.

---

### Post by NickJones on 2010-03-16
When your Windows computer is shut down impropperly or you do not dismount the HDD properly, Windows locks the disk so it can only be used in Windows, try re-starting in Windows and shutting down properly, if that doesn't work get a copy of "Partition Magic" and just format it in Windows.

---

### Post by thatdudejslate on 2010-03-17
Wow, it worked. It WOULD be something as little as that haha. Thanks!

---

