---
title: "Permissions when mounting QNAP samba share ?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by erland on 2008-08-13
I have a problem when I try to mount a Samba/CIFS share in an Ubuntu client, the share is published from my new QNAP-409 NAS.

The problem is that when I try to mount it in Ubuntu the permissions on the mounted directory is always set to 777.

Is there some way I can force the permissions so only a single user or users within a certain group has write permission to the mounted directory ?

The /etc/fstab line on the Ubuntu machine looks as follows:
//192.168.0.150/disk1    /mnt/network/qnap409/disk1      cifs    noauto,credentials=/etc/samba/credentials,uid=1000,gid=100,file_mode=0644,dir_mode=0755,iocharset=utf8  0       0

The permissions of the mounted directory looks as follows:
drwxrwxrwx 2 myuser users    0 2008-08-13 08:01 disk1

On other shares which is published from my Ubuntu server, the file_mode and dir_mode parameters works perfectly and the directories is mounted with 755 permissions, but for some reason this doesn't work with the shares from the QNAP. I'm suspecting it has something to do with unix extensions and samba/cifs. The Ubuntu server which shares works, has a smb.conf which contains "unix extensions = no", this line doesn't exist in the QNAP.

Is in not possible to control the permissions on the client side when unix extensions is enabled ?

The share on the QNAP has been created from the QNAP web interface and with permissions set to "Everyone(readonly), myuser(Full access)". The result is that it created a directory /share/HDA_DATA/disk1 on the QNAP with the following permissions:
drwxrwxrwx    2 admin    everyone     4096 Aug 13 08:01 disk1/

I suppose I can always change the permissions directly on this directory on the QNAP by logging into the QNAP with ssh, but it feels like there has to be a more user friendly way.

---

