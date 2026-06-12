---
title: "Fresh server install, can't access windows shares"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by battyice on 2007-02-21
I just finished a Ubuntu 6.06 server install with a basic gnome install.  Samba server and client is installed, and I have shares on the server that I can access from my windows machine.  The problem is that I can't access the windows machine from the linux server.  

If I try to browse the network it just says smb://xx.xx is not accessible.  I have checked everything I can think of with no luck.  Any suggestions?

---

### Post by Strider on 2007-02-21
Verify you have smbfs installed.  I don't think it's installed by default.  If you think you have smbfs installed, go to the command line and run "smbmount". 

-Mike

---

### Post by battyice on 2007-02-22
Smbfs is installed, still no luck.  I have checked everything I can think of.

I have a debian machine on the network that can browse the workgroup shares just fine, and the windows machine can access the shares on my ubuntu server...just not the other way around.

I have all the samba packages installed, is there a gnome package I'm missing?  

I only install gnome-core and gnome-utilities in addition to the basic server install and samba packages.

---

