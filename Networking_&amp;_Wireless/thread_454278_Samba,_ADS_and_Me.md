---
title: "Samba, ADS and Me"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by shonen on 2007-05-25
Alrighty, 

Thanks to the awesome support of the Ubuntu Community, I have been successfully able to hook up my Samba server through to our ADS at work and making it simply that easy for some people to access a share.

What i would *LIKE* to do is this, 


I want to have two shares, one for backups and one for general public use. My question is this:

Is there a way currently in SAMBA, where i can set backup as a "root" only folder (aka only the IT department can access the backup folder) and the public folder is open to all other users including root :)


Thanks for your help guys! 

~shonen

---

### Post by jonallport on 2007-05-25
Hi Shonen,

Assuming the ADS integration is working properly you can easily use your ADS/Windows/Domain usernames/groups for permissions on Samba shares.  Below is an example from one of my live servers:

[global]
        netbios name = CORPSERVER
        workgroup = MYCORP
        password server = *
        browseable = yes
        security = ADS
        idmap uid = 10000-20000
        idmap gid = 21000-25000
        domain logons = No
        domain master = No
        realm = MYCORP.NET
        template homedir = /home/%D/%U
        template shell = /bin/bash
        winbind refresh tickets = yes
        server string =
        load printers = No
        show add printer wizard = No
        printing = BSD
[admins]
        path = /shares/admins
        read only = no
        create mask = 0770
        directory mask = 0770
        valid users = +MYCORP\admins
        force group = +MYCORP\admins
[allusers]
        path = /shares/allusers
        read only = no
        create mask = 0770
        directory mask = 0770
        valid users = "+MYCORP\Domain Users"
        force group = "+MYCORP\Domain Users"
[public]
        path = /shares/public
        read only = yes
        public = yes

In this example my Samba server is sittings in an Active Directory (using Winbind) and uids are assigned in [global] for the Windows users/groups

There are 3 shares defined as follows:

admins = members of 'admins' domain group, files/folders created in this share are owned by the group and are exclusive t the superuser and that group
allusers = similar to the above but access granted to the (default) domain users group, users must be domain-authenticated to access it
public = read-only share available to all (even unathenticated/guest) users

Important things to note:
Use of '+' prefix for domain groups denotes that user must be a member of that groups for those rights to be applied, else access denied.
Mulitple shares can be defined for the same path, i.e. the path can be that same for multiple shares but right granted on group membership

I hope that helps, otherwise there are plenty of HOW-TOs available for the Samba suite

---

