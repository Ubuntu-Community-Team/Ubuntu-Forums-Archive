---
title: "samba printer file shareing ??????"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by weirdfate on 2008-04-15
hello people i am having one more problem that i need to resolve before i go an change my entire network to linux just 2 machines my laptop and home pc.  I was wondering why xubuntu is giving me problems with file/printer sharing.  when i go to aplications.system.shared folder  it prompts me to install samba or NFS.  I put checks in both services and click install but it keeps comming back saing to install it..  What is the problem??? Im at a loss as to why or if there is an easyer way to share files and printers with a windows machine


the printer is on the windows machine
and i want to share files from and toboth machines

---

### Post by superprash2003 on 2008-04-16
try to install by going to terminal and typing **sudo apt-get install samba smbfs**
Also follow this tutorial on setting up samba [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

---

### Post by Iowan on 2008-04-16
> **weirdfate said:**
> ... What is the problem??? 
FYI:
The problem is that Samba-client comes pre-installed, so you can (theoretically) see Windows shares from Ubuntu.  Samba-server (required to share files FROM Ubuntu) is not already there - although the smb.conf file already exists.

---

