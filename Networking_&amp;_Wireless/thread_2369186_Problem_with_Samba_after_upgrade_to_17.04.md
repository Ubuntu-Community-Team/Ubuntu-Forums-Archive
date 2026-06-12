---
title: "Problem with Samba after upgrade to 17.04"
date: 2017-08-19
forum: Networking &amp; Wireless
---

### Post by bouqui on 2017-08-19
After upgrading to Ubuntu 17.04 from 16.04 I tried to use my printer and this did not work. I removed it and tried to reinstall it without success. 

I did 

```

sudo apt-get autoremove samba
sudo apt-get purge samba 
sudo apt-get install samba

```

Same problem. Here is what I obtain if I do a status smbd

```

sudo status smbd
status: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

```

Here is what
```
testparm -s
```

returns

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

```

Here is what ```
sudo /etc/init.d/smbd status 

```

returns:

```
smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2017-08-19 19:17:00 CEST; 8min ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
 Main PID: 5606 (smbd)
   Status: "smbd: ready to serve connections..."
    Tasks: 4 (limit: 4915)
   CGroup: /system.slice/smbd.service
           &#9500;&#9472;5606 /usr/sbin/smbd
           &#9500;&#9472;5607 /usr/sbin/smbd
           &#9500;&#9472;5608 /usr/sbin/smbd
           &#9492;&#9472;5610 /usr/sbin/smbd

août 19 19:17:00 EliteBook systemd[1]: Stopped Samba SMB Daemon.
août 19 19:17:00 EliteBook systemd[1]: Starting Samba SMB Daemon...
août 19 19:17:00 EliteBook systemd[1]: smbd.service: Supervising process 5606 which is not our child. We'll most likely not notice when it exits.
août 19 19:17:00 EliteBook systemd[1]: Started Samba SMB Daemon.
```

I don't know anything to Samba, I found those instructions on other threads about Samba but don't know what this means. I have to say I am really stuck on this,
any help would be very welcomed.

---

### Post by bouqui on 2017-08-20
An update: there is a mistake at the end of the installation of Samba:

```
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory


```

---

