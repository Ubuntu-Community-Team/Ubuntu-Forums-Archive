---
title: "Ubuntu Machine not Connecting to Windows Share"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by arnold.pietersen on 2007-11-27
I have set up a Windows XP computer with a shared printer connected to it.  I use to print to it in the past from my Ubuntu laptop with no hassles and without having setup up anything. It somehow worked  "out of the box".  

Now lately I have been asked for username and password if I want to connect to the Windows XP computer. I am not able to retrace my steps in terms of where it could have gone wrong.

The Windows shared computer is called PRINT-COMPUTER within the CECS workgroup with a DHCP of 192.168.10.101

The laptop's hostname is arnold with a DHCP of 192.168.10.102

What is a minimal smb.conf file content in order to access the shared computer?  At the moment I have the following in smb.conf:

[global]
netbios name = arnold
workgroup = CECS
security = share
name resolve order = lmhosts hosts

Is the above correct?  Is there anything I should add or change on the Windows XP machine or in the smb.conf file.

Thanks in advance

Arnold

---

### Post by csat on 2007-11-27
Hi

Is this thread similar to what you have in mind?  

[http://ubuntuforums.org/showthread.php?t=624223](http://ubuntuforums.org/showthread.php?t=624223)

---

