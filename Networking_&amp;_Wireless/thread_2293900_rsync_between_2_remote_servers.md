---
title: "rsync between 2 remote servers"
date: 2015-09-08
forum: Networking &amp; Wireless
---

### Post by zkab on 2015-09-08
I am trying to rsync between 2 remote servers - 'tvserver' and 'farbaute' but get permission denied.

raivo@zkab:~$ ssh -t "rajan@tv-server" rsync -rptgoDv --delete "/home/hts/.hts/tvheadend"  "jurka@farbaute:/home/jurka/my_data/BackUp/TV/TV-Headend"
rajan@tv-server's password: xxx
jurka@farbaute's password: xxx
sending incremental file list
rsync: opendir "/home/hts/.hts/tvheadend/accesscontrol" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/backup" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/bouquet" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/caclient" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/channel" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/dvr" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/epggrab" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/input" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/profile" failed: Permission denied (13)
rsync: opendir "/home/hts/.hts/tvheadend/timeshift" failed: Permission denied (13)
rsync: send_files failed to open "/home/hts/.hts/tvheadend/config": Permission denied (13)
rsync: send_files failed to open "/home/hts/.hts/tvheadend/epgdb.v2": Permission denied (13)
rsync: send_files failed to open "/home/hts/.hts/tvheadend/superuser": Permission denied (13)

When I login to 'tvserver' and list the directory that causes the error I get following:

[email]rajan@tv-server:/home/hts/.hts[/email]/tvheadend$ ls -ln
total 60
drwx------ 2 110  44  4096 mar  2  2015 accesscontrol
drwx------ 2 110  44  4096 maj 21 20:29 backup
drwx------ 2 110  44 12288 mar 23 16:49 bouquet
drwx------ 2 110  44  4096 jun 16 23:05 caclient
drwx------ 4 110  44  4096 mar  2  2015 channel
-rwx------ 1 110  44   195 maj 21 20:29 config
drwx------ 4 110  44  4096 aug 26 23:50 dvr
-rwx------ 1 110  44   193 sep  3 13:47 epgdb.v2
drwx------ 3 110  44  4096 mar  2  2015 epggrab
drwx------ 4 110  44  4096 mar  2  2015 input
drwx------ 2 110  44  4096 apr 25 09:45 profile
-rw------- 1 110 120    48 maj 21 20:29 superuser
drwx------ 3 110  44  4096 sep  4 17:24 timeshift

As I understand only owner=110 can access the files so I added my login-user 'rajan' to system-user 110 in /etc/group:

systemd-network:x:110:rajan

but still I get the same error - permission denied ...
Where have I gone wrong ?

---

### Post by SeijiSensei on 2015-09-08
You're logged in as user "rajan" on tvserver and trying to delete files owned by user "hts".  You can log in as hts, or change the permissions on /home/hts to let rajan delete files there, or put user rajan into the hts group and make sure that /home/hts has group-writable permissions.

---

### Post by zkab on 2015-09-08
> **SeijiSensei said:**
>  ... put user rajan into the hts group and make sure that /home/hts has group-writable permissions.

Thanks - now it works !!!

---

