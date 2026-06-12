---
title: "No network drive, Is something wrong with my smb.conf file?"
date: 2024-04-12
forum: Networking &amp; Wireless
---

### Post by isprins on 2024-04-12
Hi,I have tried to get samba file sharing to work using webmin,- no success.

What is wrong with my conf file?

[ATTACH]293579[/ATTACH]

---

### Post by isprins on 2024-04-13
&#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2024-04-12 09:54:40 UTC; 24h ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 2637029 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 2637033 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 4 (limit: 115702)
     Memory: 9.6M
        CPU: 1.580s
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;2637033 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;2637036 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;2637037 /usr/sbin/smbd --foreground --no-process-group
             &#9492;&#9472;2637038 /usr/lib/x86_64-linux-gnu/samba/samba-bgqd --ready-signal-fd=45 --parent-watch-fd=11 --debuglevel=0 -F

Apr 12 09:54:40 media systemd[1]: Starting Samba SMB Daemon...
Apr 12 09:54:40 media systemd[1]: Started Samba SMB Daemon.

&#9679; nmbd.service - Samba NMB Daemon
     Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2024-04-12 09:54:40 UTC; 24h ago
       Docs: man:nmbd(8)
             man:samba(7)
             man:smb.conf(5)
   Main PID: 2637042 (nmbd)
     Status: "nmbd: ready to serve connections..."
      Tasks: 1 (limit: 115702)
     Memory: 3.2M
        CPU: 2.366s
     CGroup: /system.slice/nmbd.service
             &#9492;&#9472;2637042 /usr/sbin/nmbd --foreground --no-process-group

Apr 12 09:54:40 media systemd[1]: Starting Samba NMB Daemon...
Apr 12 09:54:40 media systemd[1]: Started Samba NMB Daemon.

ls
cores                log.haken-stasjon  log.nmbd.1     log.nmbd.3.gz  log.samba-bgqd  log.smbd.1     log.smbd.3.gz
log.192.168.132.131  log.nmbd           log.nmbd.2.gz  log.nmbd.4.gz  log.smbd        log.smbd.2.gz  log.smbd.4.gz


from log.smbd:
[2024/04/12 09:49:56.241474,  0] ../../lib/param/loadparm.c:748(lpcfg_map_parameter)
  Unknown parameter encountered: "user"
[2024/04/12 09:49:56.241495,  0] ../../lib/param/loadparm.c:1895(lpcfg_do_global_parameter)
  Ignoring unknown parameter "user"
[2024/04/12 09:49:56.241763,  0] ../../lib/param/loadparm.c:1958(lpcfg_do_service_parameter)
  Global parameter guest account found in service section!
[2024/04/12 09:54:40,  0] ../../lib/param/loadparm.c:748(lpcfg_map_parameter)
  Unknown parameter encountered: "user"
[2024/04/12 09:54:40,  0] ../../lib/param/loadparm.c:1895(lpcfg_do_global_parameter)
  Ignoring unknown parameter "user"
[2024/04/12 09:54:40.239552,  0] ../../source3/smbd/server.c:1734(main)
  smbd version 4.15.13-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2021
[2024/04/12 09:54:40.240059,  0] ../../lib/param/loadparm.c:748(lpcfg_map_parameter)
  Unknown parameter encountered: "user"
[2024/04/12 09:54:40.240079,  0] ../../lib/param/loadparm.c:1895(lpcfg_do_global_parameter)
  Ignoring unknown parameter "user"
[2024/04/12 09:54:40.240356,  0] ../../lib/param/loadparm.c:1958(lpcfg_do_service_parameter)
  Global parameter guest account found in service section!

from log.nmbd:
2024/04/07 00:03:06.397990,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.
  This response was from IP 192.168.132.23, reporting an IP address of 192.168.132.23.
[2024/04/07 00:08:08.706496,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.
  This response was from IP 192.168.132.23, reporting an IP address of 192.168.132.23.
[2024/04/07 00:13:10.320923,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.
  This response was from IP 192.168.132.23, reporting an IP address of 192.168.132.23.
[2024/04/07 00:18:12.630656,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.
  This response was from IP 192.168.132.23, reporting an IP address of 192.168.132.23.
[2024/04/07 00:23:14.925375,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.
  This response was from IP 192.168.132.23, reporting an IP address of 192.168.132.23.
[2024/04/07 00:28:15.972353,  0] ../../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.132.10 for name WORKGROUP<1d>.

The only visible thing is Windows network, but it contains nothing.

I can post screenshots from webmin.

I can post screenshots from webmin if necessary.

---

### Post by Morbius1 on 2024-04-13
You've got some parameters in your smb.conf that don't belong there: one no longer exists and the other is in the wrong place. These aren't your problem however since samba will just ignore them.

Looks like your real issue is you are attempting to use NetBIOS on a server that has disabled it by design.

If the clients to this server are running Win7/10/11 install wsdd on the server:
```
sudo apt install wsdd
```
If your clients are running Linux you are pretty much hosed because of a design flaw in all Linux file managers.

Find the ip address of the server:
```
hostname -I
```
And access the server explicitly *[COLOR="#FF0000"]in the file manager[/COLOR]*: [B]smb://server-ip-addess/Mymedia
[/B]

---

### Post by isprins on 2024-04-14
I'm unfortunately on a Linux mint client.

[ATTACH=CONFIG]293613[/ATTACH]


My webmin samba setup:
[https://youtu.be/w8FjW2RERuM](https://youtu.be/w8FjW2RERuM)


testparm
Load smb config files from /etc/samba/smb.conf
Unknown parameter encountered: "user"
Ignoring unknown parameter "user"
Global parameter guest account found in service section!
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	load printers = No
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	netbios name = MYMEDIA
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb
	guest ok = Yes


[Torrentdata]
	delete readonly = Yes
	path = /Torrentdata


[Mymedia]
	path = /Mymedia


[homes]
	path = /home/haaken

---

### Post by Morbius1 on 2024-04-14
If you are going to use Connect to Server fill it out correctly:
[ATTACH=CONFIG]293614[/ATTACH]

---

### Post by isprins on 2024-04-15
Since I cant find any documentation I have to ask:

Tjener ( server obvious ) smb://192.168.132.10
type: windows share
share ( what goes here ? /Mymedia ?)
Folder: ( what goes here ?)
Domain: media
username: haaken


This apparently tries to connect,- but nothing happens.
[ATTACH=CONFIG]293625[/ATTACH]


I can find my share on my cell phone.

---

### Post by Morbius1 on 2024-04-15
Tjener: **192.168.132.10**
Type: **Windows share**
Share: **Mymedia**
Folder: ***leave it blank***

---

### Post by TheFu on 2024-04-15
Please realize that Samba/CIFS are for MS-Windows clients. For Unix clients, the better solution is to use NFS.  I think webmin can probably configure NFS without any issues.  Both CIFS/Samba and NFS can be used for the same storage, but NFS provides the native file system interfaces and honors all the expected UNIX permissions, groups, users that every Unix-based OS expects.

NFS feels like local storage when it is mounted.  That means it feels like just another local directory.
For example, 
```
$ df -Th
Filesystem                                       Type   Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4   3.5T  3.5T   29G 100% /d/D1
istar:/d/D2                                      nfs4   3.6T  3.6T   20G 100% /d/D2
istar:/d/D3                                      nfs4   3.6T  3.6T   23G 100% /d/D3
```

I removed the local mounts for the OS and home directories from that list.  You can mount the directories anywhere you like, but most people using Ubuntu and Ubuntu-snap packages probably would want them under /media/ somewhere.

Anyway, just providing another option.  NFS has been around 30+ yrs. It is very stable and fairly trivial to setup with just 1 config file on the NFS-server and the /etc/fstab on each client.  1 line in each of those files. That's it.

---

### Post by isprins on 2024-04-16
That worked!

---

