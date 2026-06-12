---
title: "No windows logon dialogue through samba"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by milesnorth on 2013-10-04
Have fairly fresh install of Kubunt 12.04 LTS 64-bit with KDE 4.11.  Got nfs shares on the NAS mounted, samba installed, and linux shares setup.  Can play blu-ray mkv's stored on the linux HTPC from windows, but can't see windows shares from samba.  Have some notes with smbtree and manual logon attempts listed below.  Logons before the reinstall worked.  Looked at half a dozen how-tos.  Not much of a network guy, though, what am I missing?

Thanks for any help,


```

sudo apt-get install libcups2 samba samba-common

smb.conf edits:
sudo nano /etc/samba/smb.conf
   workgroup = LOFT
   ...
   name resolve order = lmhosts host wins bcast
   ...
   security = user
   ...
   SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY
   ...
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755


sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/

Windows 7 sees linux shares and windows shares

ping shows windows machines

$ smbtree
Ignoring unknown parameter "SO_RCVBUF"
Enter theatre's password: 
LOFT
        \\SKYNET                        Disk Station
        \\SIGNE-PC       
        \\MICROLINUX                    microlinux server (Samba, Kubuntu)
                \\MICROLINUX\waning moon    
                \\MICROLINUX\new moon       
                \\MICROLINUX\IPC$               IPC Service (microlinux server (Samba, Kubuntu))
                \\MICROLINUX\share              File Server Share
                \\MICROLINUX\print$             Printer Drivers
        \\JACK           
        \\ENEL-PC        
        \\ELLEN-PC                      raven's roost
        \\BIGEASY        
        \\ANDROID                       Samba on Android


samba through dolphin does not pull up windows logon dialogue

$ smbclient -L //BIGEASY -U kurt
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
params.c:Parameter() - Ignoring badly formed line in configuration file: create mask - 0755
Enter kurt's password: 
Connection to BIGEASY failed (Error NT_STATUS_UNSUCCESSFUL)

```

---

### Post by milesnorth on 2013-10-17
[SOLVED]
Finally got around to relooking at this today.  The following manual logon to a windows box yielded the following error codes.

```
$ smbclient -L //BIGEASY -U kjj
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
params.c:Parameter() - Ignoring badly formed line in configuration file: create mask - 0755
Enter kjj's password: 
Connection to BIGEASY failed (Error NT_STATUS_UNSUCCESSFUL) 

```

Searching for "SO_RCVBUF" and "create mask - 0755" found two typos in smb.conf.

$ sudo nano /etc/samba/smb.conf
$ sudo restart smbd
$ sudo restart nmbd

The windows logon dialogue was back.

---

### Post by QIII on 2013-10-17
Congrats!

Please mark the thread as solved using the "Thread Tools" drop-down.

---

