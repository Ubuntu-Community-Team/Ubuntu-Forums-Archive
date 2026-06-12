---
title: "crash on unmounting shared dir"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by bro on 2007-07-07
Hi,
The situation: 2 laptops connecting to a router. Via nfs we are sharing directories. If the other laptop shuts down, I can no longer acces my /home/me because /home/me/shared_dir_mounted-here/. I cannot umount the last mentioned dir because it tells me 'device is busy'. 
Restart helps ofcourse, but we are not using that other os, so the question is:
Is there a way for ubuntu to detect and unmount such dir's painlessly when my girlfriend shuts down her laptop?

---

### Post by Mr. C. on 2007-07-07
Never place transient NFS mounts inside a critical directory, such as your home directory, or directly under /, /etc, /lib, /usr, etc.

Mount your directory under a directory such as  /mnt.

Then, make a symbolic link in your directory which targets the NFS-mounted directory in /mnt.

eg: 

mount nfsserver:/some/directory /mnt/somedirectory
ln -s /mnt/somedirectory /home/me/somedirectory

NFS mounts were not originally designed to be attached and unattached routinely, and have only workaround-like strategies to resolve unavailable mounts.

Make sure there are no processes which still have the NFS-mounted directory anywhere in their current working directory path. This takes a bit to explain how to avoid, so if you need more info, please ask.

MrC

---

