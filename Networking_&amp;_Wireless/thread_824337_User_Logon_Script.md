---
title: "User Logon Script"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by fballem on 2008-06-10
I am new to linux and ubuntu, so this may be a basic question:

I have setup an ubuntu workstation for my kids. There is an administrator ID and an ID for each of the two kids.

I also have an NAS (Network Addressable Storage) device, with separate shares.

What I would like to do is to set it up so that if the administrator logs on, then there are specific shares off of the network device that will be mounted. When the administrator logs off, then these will be unmounted. The same process should follow for each of the kids when they logon, so that they can see their own stuff, but not that of the other child, or of the administrator.

I think the concept is a User Logon Script (and probably a logoff script to unmount the shares), but I have no idea how to go about doing this. Any suggestions (or direction on where to find the information) would be much appreciated.

I have been able to get the devices to mount in the /etc/fstab file, but that is not a user specific file, and the devices do not get unmounted when a user logs off, but only when the system is shut down or restarted.

Many thanks,

---

