---
title: "missing file in tuto"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by jrev on 2005-08-20
Hi all,
I have connected my 2 PC's via a crossed cable on the Ethernet card socket RJ45
in order to share internet connection and folders or files on ubuntu 5.04 

The internet sharing is OK and I started the following tuto : (see below)

[https://wiki.ubuntu.com/NFSServerHowTo](https://wiki.ubuntu.com/NFSServerHowTo) 

Procedure

   1.     By default, the portmap service is only accessible on the local system. For NFS service to work, access must be allowed from NFS clients as well. Edit the file /etc/default/portmap and remove the -i 127.0.0.1 option from ARGS 

OK the file "/etc/default/portmap" doesn't exist on my computer but there is the 
"etc/init.d/portmap" without any -i 127.0.0.1 option after ARGS 
there is only "" after ARGS 

the portmap package is installed as well as  "nfs-common" and "nfs-kernel-server"

where is the fault ?

Is this modification to be done on the NSF server only ?

Thanks for your help

---

### Post by jrev on 2005-08-20
This tuto hasn't been updated or corrected for the present ubuntu Hoary 5.04
did anybody solve that problem ?

Matthew Caron proposed a solution to the community.
Had he got any answer ?

---

