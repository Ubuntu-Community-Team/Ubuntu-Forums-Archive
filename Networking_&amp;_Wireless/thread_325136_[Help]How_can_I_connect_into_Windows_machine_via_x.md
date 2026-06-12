---
title: "[Help]How can I connect into Windows machine via xubuntu"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by esixth on 2006-12-25
machine A:
xubuntu 6.06
ip:192.168.0.1

machine B:
winxp
ip:192.168.0.2

"ping" is ok,"smbclient" worked fine too.

now I want mount a shared directory,so it can work like a local directory.
however it's to say,how can access "//192.168.0.2/share" like access "/mnt/mshome/Bshare"

or access //192.168.0.2/share use like "smb://"?

---

### Post by pandu.rs on 2006-12-25
install smbfs and then u can mount smb shares!

---

### Post by blackmh on 2006-12-25
smbfs! 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

