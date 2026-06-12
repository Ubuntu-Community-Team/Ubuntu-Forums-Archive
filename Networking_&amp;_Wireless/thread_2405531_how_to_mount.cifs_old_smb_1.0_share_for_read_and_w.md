---
title: "how to mount.cifs old smb 1.0 share for read and write ??"
date: 2018-11-07
forum: Networking &amp; Wireless
---

### Post by nozombian on 2018-11-07
Hello, I'm struggling with mounting SD card inserted to rather old HP printer. After trial and error, this gives me at least read access:

```
me@linux:~$ sudo mount.cifs -v -o "username=guest,password=,sec=ntlm,vers=1.0,nounix,noperm,iocharset=utf8,rw,uid=1000,gid=1000,noauto,file_mode=0777,dir_mode=0777" //10.0.0.10/memory_card ./mnt
mount.cifs kernel mount options: ip=10.0.0.10,unc=\\10.0.0.10\memory_card,sec=ntlm,vers=1.0,nounix,noperm,iocharset=utf8,noauto,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,user=admin,pass=********
me@linux:~$ sudo echo test > ./mnt/test
bash: ./mnt/test: Permission denied
me@linux:~$ ls -la ./mnt
total 1983999
drwxrwxrwx  2 me sambashare      0 zá&#345;  2  1970  .
drwx------ 32 me me          12288 lis  7 16:12  ..
drwxrwxrwx  2 me sambashare      0 úno  3  2014  HPCM2320

```

From windows 10 I can access full SD card with read/write fine (cough, cough, after enabling SMB 1.0). The share is public, without any password.

Any ideas how I can write to the share? Printer allows scan pages to SD card, which is what I'm doing, then I mount share, I copy scans to my PC and then I'd like to delete them from SD card, which is what I cannot do right now on my linux pc :-(

Thank you.

---

