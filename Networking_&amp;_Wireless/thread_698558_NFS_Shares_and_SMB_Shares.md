---
title: "NFS Shares and SMB Shares"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2008-02-16
I'm not understanding any of this, and I've managed to read several posts and threads on the subject, but to no avail. I'll explain my problem, and hoepfully someone will give me an idea of what I could do about it.

I've got a Dell Inspiron laptop, uses Ubuntu Gutsy only.
I've got a massive desktop tower, uses Ubuntu Gutsy only.
Inside the laptop I have files in the /home folder I wish to share, so that the desktop can see them and copy them.
Inside the desktop I have a huge library of files (movies, countless gigs of music, saved stuff, pictures, etc) that I wish to share to any laptop that comes to my house.

The process I've followed is simple: I've opened System/Administration/Shared Folders, and I've basically selected the folders I wanted to share, so that they look like this:
```
path: /home/sebastien
Share through: Windows networks (SMB)
Name: Desktop-Home
comment: home-folder
read-only: unchecked
```
This should open a share through Samba, readable to all who are allowed acces through my DLink router (which requires a WPA password). This means that the Samba server should publish the info so that when my Laptop is turned on, I should go into Places/Networks/WindowsNetworks/mshome/ and I should see Desktop-Home right there.
I don't see it. In fact, the laptop finds nothing there - not even WindowsNetworks.

I've tried switching the shares to NSF, but even worse - there's no NETWORK detected.
I've also tried looking for some shares that were made by Ubuntu: /var/lib/mythtv/music, but I can't see those either. I do have MythTV installed and configured, it's never run properly, but I should normally see them manually, right?

So what am I doing wrong? Seems to me this is supposed to be everything. I'm sure there's a faulty config somewhere, but I can't find anything. If anyone has some idea of what I have to do, please tell me. 

Preferrably, I'd like my Desktop to share my home folder and the entire SDB1 drive, accessible through the media folder. This is already mounted in Ubuntu and is an NTFS drive.
I would like to share both of those on both NFS and Samba... so that I can use NFS which is more efficient (or so I've heard) and share to anyone that comes in with a Windows-based machine through Samba. Both Samba and NFS shares should be read-write, accessible to all, so long as they have access to my router.

As for the laptop, I would need it to share only to my Desktop, so I'd need it to have passwrod access on each share, and the shares should only exist in NFS - although I want to be able to pass along some files to a Windows network if I am in the presence of one.

Anyone who can help me, I'll be very greatful - this has been the hardest problem I've faced yet, with no success so far.

---

### Post by couzin2000 on 2008-02-19
3 days and no answer...

---

### Post by dmizer on 2008-02-19
for sharing files through samba, see the first link in my sig. HOWEVER, use the following smb.conf file instead of the one given in the howto (this will allow you to share to any computer connected to your network without having to add users and passwords every time):

```
[global]
    ; General server settings
    netbios name = [COLOR="Red"]YOUR_HOSTNAME[/COLOR]
    server string =
    workgroup = [COLOR="Red"]YOUR_WORKGROUP[/COLOR]
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = [COLOR="Red"]/shared/files/path[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR] 
```

red text highlights the portions of the configure file that you will have to edit to match the needs of your own server.

for sharing files through nfs, follow the last link in my sig.

---

