---
title: "Samba server inaccessible by only one client after adding authentication"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by Dáire Fagan on 2016-02-22
I set up samba running on my Ubuntu 15.10 desktop and I was able to access it from my Samsung TV fine until I changed the server so that a username and password is required. Crucially here, my Android tablet and XBMC box are able to access the same samba share fine with the same username and password. The Samsung Smart TV just displays an empty directory 'Media', which is the name of the share and the folder that I have shared. Within media it should display the sub directories Video, Gallery, and Audio. 

Please can you tell me what I can try to make it work or even if there is some way to view a samba error log to try and work out the issue? I tried viewing the log with:

```
tail -f /usr/local/samba/var/smbd.log
```

```
tail -f /usr/local/samba/var/nmbd.log
```

..but those files do not exist.

How I set everything up:

```
apt-get install -y samba samba-common python-glade2 system-config-samba
cp -pf /etc/samba/smb.conf /etc/samba/smb.conf.bak
rm -rf /etc/samba/smb.conf
sudo touch /etc/samba/smb.conf

```

```
addgroup sambagroup
useradd sambauser -G sambagroup
smbpasswd -a sambauser
```

- > 12 character cryptic password entered

```
mkdir -p /media/dusf/HDD2/Media
cd /media/dusf/HDD2/
chmod -R 0770 Media
chown root:sambagroup Media
```

/etc/samba/smb.conf:

```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
dns proxy = no

#============================ Share Definitions ==============================

[Media]
path = /media/dusf/HDD2/Media
valid users = @sambagroup
guest ok = no
writable = yes
browsable = yes
force user = dusf
```

On the samsung Smart TV I edited the file smb_userdata to:

```
USER="sambauser" #or your login name
PASSWD="the same > 12 character cryptic password setup in smb.conf on the server" #password
SERVER="192.168.1.2" #IP of your samba server
SHARES="Media" #your network shares, divided with space
```

* Again this all worked fine when the server was set up to allow anonymous login, and when I had smb_userdata set up with either no username and password, or the username Anonymous.

---

### Post by Dáire Fagan on 2016-02-22
This was resolved by editing the username and password in /mnt/etc/init.d/04_04_samba.init on the Samsung TV.

---

