---
title: "SMB-connectivity problems"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by holunde on 2008-06-24
I have a question regarding file-permissions using the linux-cifs-client

I'm using Ubuntu 8.04 and right now I'm using the fusesmb utility to access shares on samba servers. This works fine, but it's a little aggressive regarding network traffic. Ubuntu's built in fuse-gvfs solution is not good enough, because quite a few programs won't load/save files using this, firefox for example.
Therefore I thought that the right way, should be to use the cifs-client.
I think the responsible module in Ubuntu is "smbfs" cersion 3.0.28a-1ubuntu4.2.
Example: I want to access files on the following share on a samba-server (3.0.21) - security on the server is USER.

comment = Edb
path = /home/afdeling/edb
read only = no
force group = edb
create mask = 660
directory mask = 770
valid users = +edb

I put the following in /etc/fstab

//ESERVER/edb /mnt/edb cifs credentials=/root/.smbinfo,uid=1000,gid=1000,iocharset=utf8  0   0        

The share mounts just fine using the username "ho" and password from the .smbinfo-textfile.
The problem is, that if I save a file on the share

-rw--w----    1 ho       edb             6 Jun 22 21:38 TEST.txt

It should have had -rw-rw--- User and group is correct.

If I create a directory

drwx------    2 ho       edb          4096 Jun 22 21:38 TEST

This should have been drwxrwx---. User and group is correct.
I've tried using different combinations of mounting parameters, such as ,file_mode=0660,dir_mode=0770, but it doesn't seem to have any effect. The result is always the same.

Am I missing out on something simple here?? Or is cifs buggy. And shouldn't the files and directories on the server be controlled by the server settings, that would be the most sensible, it seems to me.

Hans Otto Lunde
Egmont Højskolen
Denmark

---

### Post by maks_zbogar on 2008-11-29
Hi,
I'm new to Ubuntu, so I don't know many things about other systems for network shares.
Well, I just want you to know that I use gvfs. And yes there is many programs that don't show network locations in Save As dialog box. But you can trick this programs (like for example firefox):

1. goto Save As dialog 
2. delete all characters of suggested file name
3. in file name enter folder location:

/home/your_user_name/.gvfs/your_network_share/

4. after that you will see all your network computers
5. browse to desired location and enter real name of file you want to save

This (/home/your_user_name/.gvfs/your_network_share/) I also entered in Wine's drive config, so I can save to my network from any wine programs too.

---

