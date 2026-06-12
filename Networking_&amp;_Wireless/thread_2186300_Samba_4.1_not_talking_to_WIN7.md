---
title: "Samba 4.1 not talking to WIN7"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by yoyorhino on 2013-11-06
First off I want to admit I am new to this whole environment and am trying to learn! 

I am replacing my whole network, hardware and software.  I have 2 server heads that are connected with a NAS for storage.  I am running Proxmox 3 for my virtual ware.  

I have a new VM running Ubuntu 12.04.3 that I am setting up to replace my current system.  I am trying to get Samba and OpenLDAP to work so I can connect WIN7 machines.

I installed OpenLDAP and Samba 4.1, but it doesn't seem to be working correctly. 

Don't know if this is an issue, but when I check which version of samba I am using I get 4.1, but when I run another command I says Samba 3.6.3.  Duncan is the new system and Vimes is the one that it is replacing.  Thank you in advance!!!  

root@duncan:~# samba -V
Version 4.1.0
root@duncan:~# /usr/local/samba/bin/smbclient -L localhost -U%
Domain=[TVBDOMAIN] OS=[Unix] Server=[Samba 3.6.3]


        Sharename       Type      Comment
        ---------       ----      -------
        sysvol          Disk
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (Samba 3.6.3)
Domain=[TVBDOMAIN] OS=[Unix] Server=[Samba 3.6.3]


        Server               Comment
        ---------            -------
        DUNCAN               Samba 3.6.3


        Workgroup            Master
        ---------            -------
        TVBDOMAIN            DUNCAN
        VBDOMAIN             VIMES

---

