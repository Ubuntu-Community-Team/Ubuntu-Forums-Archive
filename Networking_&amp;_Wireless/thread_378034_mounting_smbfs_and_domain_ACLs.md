---
title: "mounting smbfs and domain ACLs"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by MMoose on 2007-03-06
Hi All,

I've successfully managed to mount a samba share on a windows box using this command:

sudo /bin/mount -t smbfs //192.168.1.158/Home  -o credentials=/etc/samba/credentials,workgroup=TESTDOMAIN,acl /mnt/Home

This works great. I do an ls and I see my files listed. Example:

drwxr-xr-x 1 root root  4096 2007-02-23 10:37 TestDir

The issue that I'm having is that I want to view the windows ACLs of these files. I was hoping getfacl would help:

mcrossley@rmvl0545-linux:/mnt/Home/IT$ getfacl TestDir
# file: TestDir
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

These are not the domain permissions for this file, though. I have checked with the smbcacls tool:

mcrossley@rmvl0545-linux:/mnt/Home/IT$  smbcacls -U administrator //192.168.1.158/Home TestDir
Password: 
REVISION:1
OWNER:BUILTIN+Administrators
GROUP:TESTDOMAIN+Domain Admins
ACL:TESTDOMAIN+Domain Admins:ALLOWED/19/FULL
ACL:TESTDOMAIN+MIS:ALLOWED/19/FULL

That's great, but it is not a great tool to use. Does anyone have any hints for this? I'm kind of stuck, and it would be a great help if anyone can help me out!

Thanks,
MM

---

