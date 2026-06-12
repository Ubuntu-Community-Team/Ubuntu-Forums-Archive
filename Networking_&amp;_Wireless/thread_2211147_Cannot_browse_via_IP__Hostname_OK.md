---
title: "Cannot browse via IP / Hostname OK"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by mark56 on 2014-03-14
All,

I've been running an Ubuntu RAID Array/server for about a year now, and have been using it to serve up media to a variety of media devices (Win7 w/XBMC, RPi w/Raspbmc, WDTV's via Serviio, and on... )
I had everything up and running, sharing and browsable just fine till I made some recent changes.

I originally setup my "Samba?" shares via KDE using Dolphin by right clicking and sharing out folders, and it seemingly worked.  
Having made some recent changes though, so I could modify files from my Windows PC, I seem to have invoked password hell instead of password free carelessness.
Digging around, I now see in smb.conf that none of my Samba shares are or ever were there?  So I'm wondering what I even had working in the first place.

Now, I can get to the shares if I browse by hostname, but not IP.  \\server works (no username/pass asked for), \\192.168.0.101 prompts for username and password (even if I enter the whole path to the share \\192.168.0.101\Movies ).

All clients/servers/PC's are in the workgroup WORKGROUP too.  I keep seeing that come up with Samba issues.

I have added one of the shares into the smb.conf file to start testing/working through this.

From my smb.conf file:

```

[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    encrypt passwords = true
    public = yes
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    writeable = yes
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    revalidate = yes
    workgroup = WORKGROUP
    valid users = user1,user2,user3
    syslog = 0
    create mode = 775
    usershare allow guests = yes
    panic action = /usr/share/samba/panic-action %d
    max log size = 1000
    directory mode = 775
    pam password change = yes
    security = user
    map to guest = Bad User

```

```

[Movies]path = /storage/Media/Movies
comment = Movies
writable = yes
browsable = yes
read only = no
guest ok = yes

```

Any assistance/suggestions would be appreciated.  The shares just need to be openly and freely readable by all the different clients (via IP is a must due to XBMC using MySQL database for library).

---

