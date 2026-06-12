---
title: "nautilus network places protocol"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by stonerhash on 2008-03-23
Hi there 

I have the following problem. When I try to copy files from network places "Gnome->Places->Network"
I have a network transfer speed of approximately 2,5MB/S this speed matches the smbfs protocol speed.
On the other hand when I mount the same share with CIFS I can reach 10-12MB/s

Is the anyway to change the protocol of nautilus network places ?I am pretty sure that nautilus uses smbfs and i want to change it to cifs

---

### Post by jetsam on 2008-03-23
I don't think there's any way of doing this in Nautilus itself.

If you use Nautilus to browse a share that you've mounted with cifs, though, the network transfer will go through cifs.  You could mount your share permanently in your fstab and then access it through the file system mount point  instead of accessing it through places-->network.  

They're re-doing the entire middle layer of the way Nautilus accesses network shares for Hardy.  The release is a ways away, though, and I'm not sure if performance has improved or not.

---

