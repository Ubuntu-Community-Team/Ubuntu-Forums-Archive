---
title: "CIFS mount fails - Unable to find suitable address"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by PeterTaps on 2013-09-12
Folks,

I have a share created on a Windows 7 machine.

On another Ubuntu machine, I try the following command and it works:

$ sudo mount -t cifs //192.168.1.101/mydev ./mydev -o username=myname,password=mypass

However, when I try the same command on one more Ubuntu server, it doesn't work. The error I get is "Unable to find suitable address."

When I run dmesg, I see:

CIFS VFS: Error connecting to socket. Aborting operation.
CIFS VFS: cifs_mount failed w/return code = -113

Here are the only differences between the two Ubuntu machines:
Ubuntu version - 12.04 on working machine and 13.04 on non-working machine
Location: The working machine is a physical machine in the same subnet. The non-working machine is a virtual machine (VMWare) on the same Windows machine.

I am wondering if vmware itself is playing any tricks. The network adapter is set for "bridged" networking and I am able to ping between all the 3 machines.

Thank you in advance for your help.

Regards,
Peter

---

