---
title: "cifs partition reporting as 100% full"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by PaulA999 on 2011-07-21
Hi All,
This is my first post and I am a relative newbie to Ubuntu, so I hope you will excuse any obvious oversights on my part.
 
I am running Lucid server (for a Moodle install) and have sucessfully mounted a cifs partion that resides on a Win 2008 Server to be used for backup purposes.
 
I fist tried using Webmin to backup files but have subsequently also tried using rsync.
Whatever method I try to use to copy files across I am getting an error "No space left on device 28", yet the Windows partition has over 800Gb free. The root partition on my Ubuntu server also has over 25Gb free. I have also checked /tmp and /var/tmp and am unable to find anything that might cause the problem.
 
The Windows share is mounted as follows:
//windowsserver/share$ /mnt/backup cifs credentials=/pathto/.smbcredentials,rw 0 0
 
Any pointers would be greatly appreciated.

---

