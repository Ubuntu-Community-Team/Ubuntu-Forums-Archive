---
title: "Network-HDD and Permission errors"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by kristianjohann on 2008-11-09
Hello!
I have a wireless router from Asus (WL-500gpV2). The router provides samba-services to share external hard drives. Sharing works fine:
If I open ```
smb://solarsystem-hdd/disc1_1/
``` in nautilus, then the shared disc (disc1_1) is showed. I'm able to browse through-, read and write folders, to read and write files.
If I mount the partition with ```
sudo mount -t smbfs -o guest,rw //solarsystem-hdd/disc1_1/ /media/Solarsystem-Media
```, then I'm able to browse through-, read and write folders; but I'm not able to read and write files: If I try to read a file ```
cat /media/Solarsystem-Media/test.txt
``` or to write a file ```
echo "test" >> /media/Solarsystem-Media/test.txt
```, then ```
Permission denied
``` is returned.
How to make the permissions of the self-mounted folder to read- and write-access of files (like in nautilus).
Many thanks and best regards,
Christian

---

