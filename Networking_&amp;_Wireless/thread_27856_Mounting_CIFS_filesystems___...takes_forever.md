---
title: "Mounting CIFS filesystems:   ...takes forever"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by luna6 on 2005-04-17
Hello,
I have a few computers at home, and when my linux2 box boots up, it has a few cifs remote directories to mount through samba on another linux1 computer, the problem is it takes maybe 3-5 minutes for linux2 to connect linux1 and authenticate and continue the boot (I know nfs maybe more appropriate, but I had troubles with getting nfs and my software firewalls to play nicely, so wont go there). Samba is configured to require username and password for all clients connecting to linux1, which I feel more comfortable with. In the past I did change something, and linux2 would mount the remote directories almost instantly but I cannot remember what it was I had setup to allow it to connect so quickly...any help on this issue (long time to mount samba directories) would be greatly appreciated.

Here is my smb.conf file on linux1 :


workgroup = Xpark
netbios name = Linux1
server string = Linux1 Server
hosts allow = 192.168.1.91 192.168.1.92 127.

log file = /var/log/samba/%m.log
max log size = 50

security = share
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
domain master = yes
preferred master = yes

#============================ Share Definitions ==============================
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /bin/false
winbind use default domain = no
username map = /etc/samba/smbusers
[homes]
comment = Home Directories
browseable = no
writeable = yes


[Audio-N]
path = /Lunapark/Audio-N
guest ok = yes
writeable = no
write list = userfoo,userfoo1


[Audio-A]
path = /Lunapark/Audio-A
guest ok = yes
writeable = no
write list = userfoo,userfoo1



Here is the fstab file on linux2 :

//192.168.1.90/Audio-A /Lunapark/Audio-A cifs user,password=edited,username=userfoo 0 0
//192.168.1.90/Audio-N /Lunapark/Audio-N cifs user,password=edited,username=userfoo 0 0

---

### Post by ifrflyer on 2005-04-24
I know that cifs is the new way to go; have you considered trying this very simple setup with smbfs? Try

```
sudo apt-get install smbfs
```

then change your /etc/fstab for the shares to smbfs and see if that's any better? 

Also, possibly this:

```
hosts allow = 192.168.1.91 192.168.1.92 127.
``` 

may cause you some strife. This can act as wildcards and not specific IP's. Perhaps this:

```
hosts allow = 192.168.1 127.
``` 

might be better?

If not, at least it got the thread going again!

---

### Post by luna6 on 2005-05-04
Hello,
thanks for the tip, changing the fstab to smbfs instead of cifs and installing smbfs on the host computer and opening up port 445 for smbfs did the trick...mucho gracias!

---

