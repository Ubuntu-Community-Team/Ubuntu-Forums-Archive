---
title: "Samba 4 Share not showing in Windows 7 Network Places"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by Luke_KOtarba on 2013-09-07
All,

I have an issue it might be easy but I just cant get it resolved on my end.

I have Samba 4 set up as AD DC. It is running on a Ubuntu Server 12.04 LTS. I am able to mount the share if I type [\\(server]("file://\\(server") IP)\(Share name) however I do not see the share folder or even the share machine under windows "Network".

I connected to the domain and I can ping the server. The only issue is I don't see it in "Network"

I also have a question regarding Samba 4. 
If I create a user under Windows7 using the RTS do I need to do anything under Ubuntu/samba?
Reason for asking is that I created a user named luke and I created a folder that only that user can access. However when I put his login credentials or even login to the domain as that user I am unable to access that folder.

Below is my smb.conf configuration any help is really appreciated. I will also try to resolve the issues myself because its fun.

> [global]
        workgroup = HOUSE
        realm = HOUSE.LAN
        netbios name = ZEUS
        server role = active directory domain controller
        security = user
        wins support = yes
        dns forwarder = 192.168.135.50
        dns forwarder = 8.8.8.8
# added after to see if works
        unix extensions = no
        map to guest = Bad User
        wide links = yes
        browse list = yes
#oplocks = no
        socket options = IPTOS_LOWDELAY TCP_NODELAY SO_KEEPALIVE
        write cache size = 2097152
        use sendfile = true
        getwd cache = yes
        public = yes


# END Addistions

[netlogon]
        path = /usr/local/samba/var/locks/sysvol/house.lan/scripts
        read only = No
[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No
[Users]
directory_mode: parameter = 0700
read only = no
path = /SAMBA_SHARE/data/PRIVATE/SAMBA_USERS
csc policy = documents


# ----SHARES----
[Photos]
        comment = Photos on the Server
        path = /SAMBA_SHARE/media/Photos
        read only = yes
        available = yes
        browseable = yes
        write list = luke
        guest ok = yes
        printable = no
        locking = no
        strict locking = no
        wide links = yes

 
[Videos]
        comment = Videos on the Server
        path = /SAMBA_SHARE/media/Videos
        read only = yes
        available = yes
        browseable = yes
        write list = luke
        guest ok = yes
        printable = no
        locking = no
        strict locking = no
        wide links = yes
# PRIVATE USER FOLDERS
[Luke]
        comment = Luke Private User folder
        path = /SAMBA_SHARE/data/PRIVATE/Luke
        read only = no
        writable = yes
        printable = yes
        browseable = yes
        valid users = luke



Thank you for everything.

---

