---
title: "Performing Backups with Rsync and Cron"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ego1 on 2008-05-06
I am going to become crazy with this problem.
I need get some folder from a windows remote server, and I'd made this file

~/backups/backupSAGE.sh

#//bin/bash -xv

mount.cifs //10.1.50.201/c$ /home/elder/montaje -o ro,username=administrator,password=password,iochar set=utf8,codepage=cp850sudo
sleep 5
#ls /home/elder/montaje/backupSAGE/
rsync -avz --bwlimit=50 /home/elder/montaje/backupSAGE/ /home/elder/backups/backupSAGE
sleep 5
umount.cifs /home/elder/montaje

elder@pcelder:~/backups$ ls -la backupSAGE.sh
-rwxr-xr-x 1 elder elder 320 2008-05-01 13:41 backupSAGE.sh
elder@pcelder:~/backups$

this file is running from sudo crontab

elder@pcelder:~$ sudo crontab -l
[sudo] password for elder:
# m h dom mon dow command
0 21 * * Mon-Fri sh /home/elder/backups/backupSAGE.sh > /home/elder/backups/backupSAGE.log

I need to run this task as root because the mount command.

If I activate the ls command and deactivate rsync I get the list of files in the log file. If I deactivate the ls command and activate rsync I get a empty log file, and the transfer no happen.

If I make a manual running

elder@pcelder:~$ cd backups/
elder@pcelder:~/backups$ sudo sh ./backupSAGE.sh
[sudo] password for elder:
building file list ... done
./
Inter, Inc_-031908.ptb
Inter, Inc_-032008.ptb
Inter, Inc_-032108.ptb
Inter, Inc_-032508.ptb
Inter, Inc_-032808.ptb

I don't have /etc/cron.allow neither /etc/cron.deny so I beleive root is the unique personality able to run crontab.

I appreciate some help
Elder

---

