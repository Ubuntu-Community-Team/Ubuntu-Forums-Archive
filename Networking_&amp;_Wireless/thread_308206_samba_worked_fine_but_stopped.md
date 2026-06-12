---
title: "samba worked fine but stopped"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2006-11-27
so, the title pretty much says it all. though it took me awhile to get it off the ground, i haven't had any problems sharing files with my Windhoes computer until now. the XP machine says that the folder and/or path (eg the one that's being shared via smb) is invalid. of course, it is. the only thing i've changed on my ubuntu computer is at System > Admin > Networking, i switched the location (to use a different wireless network) but have since switched it back.

i'm about 99% sure that my samba conf file is solid. but, how can i make sure that all the necessary daemons are running?

---

### Post by mssever on 2006-11-27
You can use ```
ps -ef | grep smbd
``` to see if smbd is running. Other than that, consider this a complimentary bump. :)

---

### Post by dbbolton on 2006-11-27
danke. what's a bump?

```

daniel@daniel-laptop:~$ ps -ef | grep smbd
root      6838     1  0 23:14 ?        00:00:00 /usr/sbin/smbd -D
root      6841  6838  0 23:14 ?        00:00:00 /usr/sbin/smbd -D
daniel    7156  6725  0 23:20 pts/1    00:00:00 grep smbd

```

no idea what that means :)

```

daniel@daniel-laptop:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[samba]"
Loaded services file OK.
WARNING: lock directory /var/run/samba should have permissions 0755 for browsing to work
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = BOLTON
        server string = daniel-laptop
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[MyFiles]
        path = /home/samba/
        force user = daniel
        force group = daniel
        read only = No
        create mask = 0644
        guest ok = Yes

[samba]
        comment = shared
        path = /home/samba
        read only = No
        guest ok = Yes

```there's the result of "sudo testparm"

what are those errors?

---

### Post by mssever on 2006-11-27
> **dbbolton said:**
> danke. what's a bump?
A bump is when you reply to a thread for the purpose of moving it up in the list of threads so that more people will see it.
> ```

daniel@daniel-laptop:~$ ps -ef | grep smbd
root      6838     1  0 23:14 ?        00:00:00 /usr/sbin/smbd -D
root      6841  6838  0 23:14 ?        00:00:00 /usr/sbin/smbd -D
daniel    7156  6725  0 23:20 pts/1    00:00:00 grep smbd

```no idea what that means :)
It means that the samba daemon is up and running.
> ```

daniel@daniel-laptop:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[samba]"
Loaded services file OK.
WARNING: lock directory /var/run/samba should have permissions 0755 for browsing to work
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = BOLTON
        server string = daniel-laptop
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[MyFiles]
        path = /home/samba/
        force user = daniel
        force group = daniel
        read only = No
        create mask = 0644
        guest ok = Yes

[samba]
        comment = shared
        path = /home/samba
        read only = No
        guest ok = Yes

```there's the result of "sudo testparm"

what are those errors?

The lock directory permissions error might be causing your problems (just a guess). It's easy to fix, though. Just do ```
sudo chmod 0755 /var/run/samba
```

---

### Post by dbbolton on 2006-11-28
it's working now. thank you

---

