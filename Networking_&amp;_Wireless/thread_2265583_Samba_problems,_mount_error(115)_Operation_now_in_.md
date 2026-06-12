---
title: "Samba problems, mount error(115): Operation now in progress"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by pekka2 on 2015-02-16
My Samba suddenly stopped working.

I have a samba server, called mjolnir, at 192.168.1.22, running ubuntu 14.04, and a client, running Mint 17.1.

Fstab is as follows:
```
#SAMBA
//192.168.1.22/ptahome    /home/pekka/pta_mjolnir        cifs    credentials=/home/pekka/.smbcredentials,noexec 0 0
//192.168.1.22/mjolnir-rw    /home/pekka/mjolnir        cifs    credentials=/home/pekka/.smbcredentials,_netdev 0 0
//192.168.1.22/htahome    /home/heli/hta_mjolnir        cifs    credentials=/home/heli/.smbcredentials,_netdev 0 0
//192.168.1.22/music    /media/Music        cifs    guest,_netdev 0 0
//192.168.1.22/pics    /media/Pics        cifs    guest,_netdev 0 0
```

The samba shares are not mounted at boot. When I try to mount them with "sudo mount -a", I get this:

```
pekka@Gungnirmint ~ $ sudo mount -a
[sudo] password for pekka: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Mounting with smbclient also fails:
```
pekka@Gungnirmint ~ $ sudo smbclient -L 192.168.1.22 -U pta
Enter pta's password: 
Connection to 192.168.1.22 failed (Error NT_STATUS_IO_TIMEOUT)
```

I can ping the server:
```
pekka@Gungnirmint ~ $ sudo mount -a
[sudo] password for pekka: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

On the server, testparm gives this:
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[music]"
Processing section "[pics]"
Processing section "[mjolnir]"
Processing section "[ptahome]"
Processing section "[pinjahome]"
Processing section "[htahome]"
Processing section "[mjolnir-rw]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
    server string = Oxbacka-samba
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts, host, wins, bcast
    dns proxy = No
    idmap config * : backend = tdb
    hosts allow = all

[music]
    path = /home/pta/public/Musaa
    guest ok = Yes

[pics]
    path = /home/pta/public/Kuvia
    guest ok = Yes

[mjolnir]
    path = /mjolnir
    guest ok = Yes

[ptahome]
    comment = Pta-home
    path = /home/pta
    valid users = pta
    read only = No

[pinjahome]
    comment = Pinja-home
    path = /home/pinja
    valid users = pinja
    read only = No

[htahome]
    comment = hta-home
    path = /home/hta
    valid users = hta
    read only = No

[mjolnir-rw]
    comment = Mjolnirw
    path = /mjolnir
    valid users = pta
    read only = No
```

I recently changed my router, this changed the ip addresses, but I think Samba has worked even after the switch. 
Not sure what to try next?

---

