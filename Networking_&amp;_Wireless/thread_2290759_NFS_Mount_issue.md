---
title: "NFS Mount issue"
date: 2015-08-15
forum: Networking &amp; Wireless
---

### Post by Martinjo84 on 2015-08-15
Hey guys

I have a little permissive issue on my owncloud clint where i have mounted a NFS share.

Server setup.
Debian proxmox 
ZFS Share

```
root@pve:~# ls -la /mnt/total 78
drwxr-xr-x  7 root   root    4096 Aug 14 22:52 .
drwxr-xr-x 25 root   root    4096 Aug 11 17:18 ..
drwxrwx--x  4 nobody nogroup    5 Aug 14 23:41 owncloud

```

/etc/exports
```
/mnt/owncloud    10.0.0.14/24(rw,root_squash,no_root_squash,subtree_check)
```


Client.
/etc/fstab
```
10.0.0.5:/mnt/owncloud /var/www/html/owncloud/nfsdata nfs rw,sync,hard,intr 0 0
```

```
[root@owncloud owncloud]# ls -la /var/www/html/owncloud/totalt 145
drwxr-xr-x. 14 apache apache  4096 14 aug 23:36 .
drwxr-xr-x.  3 root   root      21 10 jun  2014 ..
drwxr-xr-x. 26 apache apache  4096 14 aug 18:35 3rdparty
drwxr-xr-x. 22 apache apache  4096 14 aug 18:35 apps
-rw-r--r--.  1 apache apache   477 14 aug 18:35 AUTHORS
drwxr-xr-x.  2 apache apache    93 14 aug 23:42 config
-rw-r--r--.  1 apache apache  2492 14 aug 18:35 console.php
-rw-r--r--.  1 apache apache 34520 14 aug 18:35 COPYING-AGPL
drwxr-xr-x. 19 apache apache  4096 14 aug 18:35 core
-rw-r--r--.  1 apache apache  5179 14 aug 18:35 cron.php
drwxrwx---.  5 apache apache  4096 14 aug 19:00 dataold
-rw-r--r--.  1 apache apache 22276 14 aug 18:35 db_structure.xml
-rw-r--r--.  1 root   root    2029 14 aug 18:53 .htaccess
-rw-r--r--.  1 apache apache   179 14 aug 18:35 index.html
-rw-r--r--.  1 apache apache  2076 14 aug 18:35 index.php
-rw-r--r--.  1 apache apache  2595 14 aug 18:35 indie.json
drwxr-xr-x.  3 apache apache    30 14 aug 18:35 l10n
drwxr-xr-x.  6 apache apache    93 14 aug 18:35 lib
drwxrwx--x.  4 nobody nobody     5 14 aug 23:41 nfsdata
-rw-r--r--.  1 apache apache   283 14 aug 18:35 occ
drwxr-xr-x.  2 apache apache    56 14 aug 18:35 ocs
drwxr-xr-x.  2 apache apache    41 14 aug 18:35 ocs-provider
-rw-r--r--.  1 apache apache  3058 14 aug 18:35 public.php
-rw-r--r--.  1 apache apache  4337 14 aug 18:35 remote.php
-rw-r--r--.  1 apache apache    26 14 aug 18:35 robots.txt
drwxr-xr-x. 13 apache apache  4096 14 aug 18:35 settings
-rw-r--r--.  1 apache apache  1727 14 aug 18:35 status.php
drwxr-xr-x.  3 apache apache    33 14 aug 18:35 themes
-rw-r--r--.  1 apache apache   190 14 aug 18:35 version.php



```


I need the right chmod and chown setting for this share, i added the no_root_squash so i thought i could chown the mounted folder, but i cant. 
What am i doing wrong?

I use this for setting up my webapp 
find /opt/lampp/htdocs -type d -exec chmod 755 {} \;
find /opt/lampp/htdocs -type f -exec chmod 644 {} \;

Have a nice weekend :)

---

### Post by Martinjo84 on 2015-08-15
I had [COLOR=#000000][FONT=Ubuntu Mono]root_squash,no_root_squash 

Removed the root_squash, didnt help[/FONT][/COLOR]

---

### Post by Martinjo84 on 2015-08-16
It was a NFS V4 issue, using v3 now works

---

