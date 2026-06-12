---
title: "Problem with &quot;force user&quot; param in samba 4.3.8"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by Arturro on 2016-04-27
Hi,

Recently I have found another issue after upgrading to samba 4.3.8. For all shares with "force user" param set users have no write access. Removing this param solves problem but I want to have one owner for all the files regardless of real user. 
Previous version 4.1.6 worked with this config without problems. Any ideas?

Arturro

---

### Post by Morbius1 on 2016-04-27
4.3.8 has a lot of issues but I haven't experienced a problem with "force user".

You might want to post the output of the following commands so folks here can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Arturro on 2016-04-27
> **Morbius1 said:**
> You might want to post the output of the following commands so folks here can see how you are set up

This is my setup, nothing special :)

Load smb config files from /etc/samba/smb.conf
Processing section "[Downloads]"
Processing section "[Pictures]"
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
        workgroup = X.LOCAL
        server string = Samba Server
        obey pam restrictions = Yes
        guest account = nobody
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = hosts wins bcast
        load printers = No
        show add printer wizard = No
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Downloads]
        comment = Downloads
        path = /home/smb/Downloads
        force user = smb
        force group = smb
        group = smb
        read only = No
        create mask = 0644
        guest ok = Yes


[Pictures]
        comment = Pictures
        path = /home/smb/Pictures
        force user = smb
        force group = smb
        group = smb
        read only = No
        create mask = 0644
        guest ok = Yes



[homes]
        path = /home/%S
        read only = No
        browseable = No

This is testparm output. I have no user defined shares. As I mentioned earlier "Downloads" and "Pictures" are only allow writes when I remove "force user" and "force group" so this is not permissions issue. 
"Homes" works without problem.

---

### Post by Morbius1 on 2016-04-27
At the moment I don't see anything wrong with the share definitions aside from the "group" parameter which I've never seen before. googling suggested it's a synonym  for "force group". 

Maybe it's because I only deal with small networks but there's some oddities:

*** The most peculiar thing though is this shows up in testparm:
> guest account = nobody
That's a default setting and even if you added it to smb.conf testparm would not show it because it's a default. If you run testparm this way doesn't it show as a default setting and assigned to "nobody":
```
 testparm -sv /dev/null | grep "guest account"
```

The other oddity is you are missing "map to guest = Bad User" which converts the guest user to the "guest account". Without that line Samba defaults to Never which means it shouldn't have allowed the guest user access at all - depending on the client OS.

I haven't been much help I'm afraid and I'm about to lose my internet connection ( long story ) but I will see if anyone else has this issue.

---

### Post by Arturro on 2016-04-30
> **Morbius1 said:**
> I haven't been much help I'm afraid and I'm about to lose my internet connection ( long story ) but I will see if anyone else has this issue.

You are wrong :) "Map to guest" is exactly what my config need. After setting this to "Bad User" shares are available for write again. The strange thing is why Samba 4.1.6 worked with this parameter set to default?
Anyway now everythig is ok. Thak You!

---

