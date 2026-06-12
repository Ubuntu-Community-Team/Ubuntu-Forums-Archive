---
title: "NFS: Device or resource busy"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by stovocor on 2008-10-02
Hello!

On our ubuntu (8.04) machine we mount home directories from a Solaris server with NFS and autofs. From time to time users complain that they are unable to delete any directories. The error message is "Device or resource busy".

When I look with "nfsstat -m", I can see a lot of mount points for each user, including the directory which cannot be deleted. One user had a total of 200 mounts!

My question is: Why does NFS mount each directory seperately?

Here is an example output for a user:

/ldaphome/username from host:/export/username
Flags: rw,vers=3,rsize=1048576,wsize=1048576,hard,intr,proto=tcp,timeo=600,retrans=2,sec=sys,addr=host

---

### Post by jones139 on 2008-10-02
This might not be much help, but I'm pretty sure it is not NFS that is messing about, but the automounter.  Alas I haven't used automounters for years, so can't help much - I would search the web to look for solutions to automounter problems.

---

