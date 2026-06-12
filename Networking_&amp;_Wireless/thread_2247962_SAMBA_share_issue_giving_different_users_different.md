---
title: "SAMBA share issue giving different users different permissions to the same media"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by hornbutu on 2014-10-11
Hey everyone!

Im having a terrible time figuring out how to do some advanced SAMBA sharing with LXLE (lubuntu). I've installed LXLE 14.04-64 on my friends eeepc, and intend on using it as a torrent box, as well as a linux home file serve using SAMBA.

What I want to do, is set SAMBA so my friends can read/write, while his mom can only read so nothing is deleted. I am sharing the /Media directory, and will be setting 3 external USB HDD's to auto mount on startup via editing the fstab.


To test I've set a USB stick to auto mount via fstab to a folder named "test", located inside the media folder.
/Media
    L---- /cdrom
    L---- /phobos
    L---- /test

I disabled the firewall by:
```
phobos@linuxserver:~$ sudo ufw disable
[sudo] password for phobos: 
Firewall stopped and disabled on system startup
phobos@linuxserver:~$ sudo reboot
```

Once it booted back up, I logged in the samba share (via my other lxle laptop) as "nate" and "phobos" and I was still able to create and edit files and folders in the test folder.


Once I log in as "mom" I can see the contents of the media folder, but when i click on the test folder it says, "error permission denied". 


Any other thoughts? Know of a samba dedicated forum? I can post the solution here so it still betters our community! My samba config follows...

```
#======================= Global Settings =======================
[global]
workgroup = WORKGROUP
server string = phobos server
netbios name = phobos
dns proxy = no
#======================= Logging =======================
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
#======================= Sharered Folders =======================
[media]
path = /media
browseable = yes
read list = mom nobody
write list = phobos nate
create mask = 0777
directory mask = 0777
admin users = phobos nate
```

---

### Post by hornbutu on 2014-10-12
ok. so thanks to "KUKKS" on the #SAMBA IRC channel, this has been solved! 


I added all three users to group "smbusers" and then added this 
```
 force group = smbusers
force directory mode = 0770
force create mode = 0770 
```


so my config now looks like this:




#======================= Global Settings =======================


[global]
workgroup = WORKGROUP
server string = phobos server
netbios name = phobos
dns proxy = no


#======================= logging =======================
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d




#======================= Sharered Folders =======================


[media]
path = /media
browseable = yes
read list = mom,nobody
write list = phobos,nate
create mask = 0777
directory mask = 0777
admin users = phobos,nate
force group = smbusers
force directory mode = 0770
force create mode = 0770


"sudo chown -R :smbusers /media"


"id mom" uid=1001(mom) gid=1001(mom) groups=1001(mom),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),30(dip),44(video),46(plugdev),102(netdev),106(fuse),108(lpadmin),112(nopasswdlogin),119(sambashare),1004(serf),1005(smbusers)


That told me the group ID # for smbusers was 1005


edited my fstab: UUID=5C388359019E1306 /media/test ntfs-3g uid=1000,gid=1000,umask=007 0 0   <===Changed that to "gid=1005" which would be smbusers


rebooted 


"ls -ald /media/test" drwxrwx--- 1 phobos smbusers 4096 Oct 11 20:23 /media/test


logged in as mom and had could see all, and only read it! nate and phobos had full write/read/execute.

---

### Post by SeijiSensei on 2014-10-13
deleted

---

