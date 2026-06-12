---
title: "New problem with Samba FIle Share"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by andy_cowman on 2007-02-11
Hi 

Ages ago I set up a simple bit of file sharing with Samba. It worked fine between 2 normal ubuntu boxes with one machine automatically mounting a shared folder. 

It doesnt work now and I don't know why, I have tried to re make it and the message I get from my current comp on Xubuntu is this

[mntent]: warning: no final newline at the end of /etc/fstab
5091: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

and its the same from the orginal two ubuntu boxes. I have added the user details to smbcredentials, the folder is shared, and fstab has

//192.168.1.103/Vault   /home/andy/PhotoDrive smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

I checked the IP and its the right address. Both computers have been updated to edgy and also the network is on DHCP, is it worth trying static IP addresses?I dont see how it would make a difference.

Thanks

Andy

---

### Post by andy_cowman on 2007-02-11
Ok I have double checked that smbfs is installed as another post said they thought it was but it turned out it wasnt... still not working

I have installed Xsmbrowser and that will let me mount the drive? Why wont it work in fstab?

Andy

---

