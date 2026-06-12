---
title: "samba with Dapper and XP"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by davidgarcin on 2006-10-21
I'm trying to configure samba to allow all other users/computers on my home network to have anonymous read access to my shares.  Everyone else is running XP.

After googling and reading forums, I've got to the point where XP users see my computer and shares, but when they try to access them, they get "The network path was not found".  I'm not running any firewall, they have File and Print sharing enabled on the XP firewall.  I can access their shares, and they can access mine if I'm running XP (I'm dual booting).

Here's my smb.conf:
```

[global]
workgroup = Workgroup
netbios name = dave
security = share
preferred master = no
local master = no
domain master = no

wins support = no
[installers]
comment = installers
path = /media/files/installers
read only = Yes
guest ok = Yes
available = yes
browseable = yes
public = yes
writable = no
```

I have set the permissions for /media/files/installers to 774 using chmod.  (However, when I right click -> properties -> permissions, "others" still don't have read priveleges.  I don't understand that)

I have run testparm, and here's what I get:
```
root@Dave:~# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[installers]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        security = SHARE
        preferred master = No
        local master = No
        domain master = No

[installers]
        comment = installers
        path = /media/files/installers
        guest ok = Yes

```

I've restarted samba using /etc/init.d/samba restart more times than I can count.  I'm going crazy trying to make this work.  Any ideas?
Thanks,
-Dave

---

### Post by davidgarcin on 2006-10-21
small update on that... after a complete reboot, all XP computers can't see mine.  They can ping me fine, but \\Dave gives a "Network path not found"

---

