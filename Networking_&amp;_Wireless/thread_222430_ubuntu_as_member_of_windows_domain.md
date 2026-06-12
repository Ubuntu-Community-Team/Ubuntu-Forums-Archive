---
title: "ubuntu as member of windows domain"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by viveknz76 on 2006-07-25
Hi,

I have installed the samba on my machine and edited the smb.conf with the WORKGROUP=***server***. I restarted the samba but whenever I click Windows Network I get smb:/// is not a valid location.  Please help me to set the samba on my machine so that I can access the shared files on the server.

Thanks

Vivek

---

### Post by Thund3rstruck on 2006-07-25
Samba is a server for sharing files to windows machines, not for accessing shares. You need the smbtools...

```

$ sudo apt-get install smbfs

```

Once you get these you can use nmblookup, smbclient, and smbmount. Liekwise you can also 'map network shares' by using mount -t smbfs in /etc/fstab.

---

### Post by bwiewiora on 2006-07-25
I am having a similar issue--I'm trying to get my Ubuntu box on a windows domain.  I changed the workgroup setting in smb.conf to the name of my domain, but when I look for it on the Windows Server, my Ubuntu box is in a workgroup called MSHOME instead of the domain. 

Any thoughts?

---

