---
title: "printer share stopped after installing network drive"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by ogger on 2009-03-02
I somehow managed mounting my networkdrive thru CIFS, I believe, as nautilus was acting erratically. However, now I cannot access my ubuntu computer from my windows computer. This sucks because my ubuntu computer makes its printer available. 
also, whenever I click on 'windows networks' in nautilus I get the message 'Unable to mount location. Failed to retrieve share list from server.' so something must be wrong with my permissions or smb.conf???

thanks for your consideration.

BTW, here is my fstab:
proc /proc proc defaults 0 0
UUID=98d36329-a1d1-42a3-b9b2-62611b9e57be / ext3 relatime,errors=remount-ro 0 1
UUID=17c38710-f34c-4e1e-94de-abe4422debac /home ext3 relatime 0 2
UUID=2d6553f0-5077-4c2f-9079-8713448086eb none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 2
UUID="e8268b32-f7ae-4c54-a765-93acc00ab440" /media/Xtra\040Drive ext2 defaults  0 0
//192.168.1.2/Volume_1 /media/Large\040External\040Drive cifs password=[hidden],_netdev, 0 0



And here is my smb (I deleted everything with a # and ; at the beginning):
[global]
   workgroup = Peter
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   obey pam restrictions = yes
   unix password sync = yes
   load printers = yes
   usershare allow guests = yes
wins support = no
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
[peter]
path = /home/peter
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by ogger on 2009-03-03
I think there must be something wrong with authentication of my smb.conf. When I run smbclient -l Peter it says bad network name. 

Can somebody walk me through what to put intosmb.conf or post an original that works for home network and printer sharing with a Windows box (no permissions or passwords required)?

Also, I got following error during this test:
peter@peter-desktop:~$ nmblookup -d 2 "*" 
added interface eth1 ip=fe80::240:f4ff:fe49:7f34%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
querying * on 192.168.1.255
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_query failed to find name *

---

### Post by ogger on 2009-03-04
bump

---

