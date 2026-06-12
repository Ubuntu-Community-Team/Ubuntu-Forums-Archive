---
title: "fstab smbfs entries cause Input/Output error"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by cnschulz on 2008-03-16
Hello, 

I have some shares on my gutsy server (smb) that have been (are) working fine from my windows laptop.

Ive just installed a fresh 7.10 workstation and added the following line to fstab:

//192.168.1.3/audio    /mnt/audio        smbfs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/video    /mnt/video        smbfs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/photo    /mnt/photo        smbfs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/download /mnt/download     smbfs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

after adding those to fstab, i run mount -a and all is fine...

... on the next boot, when i change into the directory it takes forever (20 seconds) then when i do an ls i get and Input/Output error

the 7.10 workstation boots very slowly untill i remove the entries and reboot. its like there is a lock on those directories even after i do a umount

any ideas what ive done wrong?

:confused:

---

