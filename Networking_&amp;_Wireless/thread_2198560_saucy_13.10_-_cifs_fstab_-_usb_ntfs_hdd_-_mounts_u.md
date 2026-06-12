---
title: "saucy 13.10 - cifs fstab - usb ntfs hdd - mounts unwritable"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by herrmeier on 2014-01-09
I am not able to mount two usb hdd drives (NTFS), which are connected to my raspberry pi (raspbmc with debian wheezy) with fstab and cifs in such a way, that I am able to write from my ubuntu-laptop.

I am able to write, if I connect manually with thunar or dolphin if I search the network, using the smbusername and smbpassword.

So it should work. But what doesn't work, is to connect with fstab.

Even though
```
$ mount
//192.168.x.y/devices/INTENSO/ on /home/'ubuntuuser'/raspberry_pi/INTENSO type cifs (rw)
//192.168.x.y/devices/Elements/ on /home/'ubuntuuser'/raspberry_pi/Elements type cifs (rw)
//192.168.x.y/'piuserhome'/ on /home/'ubuntuuser'/raspberry_pi/home/'piuserhome' type cifs (rw)
```
tells me, that the shares on the raspberry pi mounted onto the ubuntulaptop with my fstab configuration should be writable...and in /etc/fstab smbuser and smbpasswd logs in...

```
# cifs INTENSO
//192.168.x.y/devices/INTENSO/ /home/'ubuntuuser'/raspberry_pi/INTENSO/ cifs noauto,user,uid=1000,gid=1000,rw,credentials=/home/'ubuntuuser'/.smbcredentials  0 0

# cifs Elements
//192.168.x.y/devices/Elements/ /home/'ubuntuuser'/raspberry_pi/Elements/ cifs user,uid=1000,rw,username='raspberry-pi-smb-username',password='raspberry-pi-smbpassword' 0 0

# cifs piuserhome
//192.168.x.y/'pihome'/ /home/'ubuntuuser'/raspberry_pi/home/'piuser'/ cifs username='raspberry-pi-smb-username',password='raspberry-pi-smbpassword,uid=1000,gid=1000 0 0
```
It just doesnt work...

Here my smb.conf of raspbmc (wheezy) on the raspberry pi:

```
$ less /etc/samba/smb.conf 
[global]
    workgroup = WORKGROUP
    #usershare allow guests = yes
    #security=share
    security=user
    follow symlinks = yes
    wide links = no
    unix extensions = no
    lock directory = /var/cache/samba
['pihome']
    browsable = yes
    read only = no
    #guest ok = yes
    valid users = 'piuser'
    path = /home/'piuser'
    #force user = 'piuser' (no longer needed)
[devices]
    browsable = yes
    read only = no
    #guest ok = yes
    valid users = 'piuser'
    path = /media
    force user = 'piuser'
```

Any ideas what I am doing wrong? Thank you already!
Cheers Hans:confused:

---

