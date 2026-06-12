---
title: "Problem Viewing Windows 7 Pro michane Kubuntu 12.04.4"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by techanimelover on 2014-02-08
both computers are using wireless 
the windows 7 machine cant see the linux machine and vise versa

---

### Post by tfrue on 2014-02-09
Do you have Network Discovery and File Sharing turned on in Windows?

---

### Post by techanimelover on 2014-02-09
yes

---

### Post by tfrue on 2014-02-10
What are the IP's and the Subnet mask of the two machines?

---

### Post by techanimelover on 2014-02-10
how do i find out that?
is it safe to post ips?

---

### Post by tfrue on 2014-02-10
```

ifconfig 
```
Will post the info on the Linux machine and:
```
ipconfig -a
``` 
Will post the info on the Windows computer.

It's safe to post IPs that are private, which are non route-able like 192.168.1.1, but not the public IP addresses. Those two commands will not give you public IPs but what is assigned to the computer by the router.

---

### Post by techanimelover on 2014-02-11
windows
192.168.1.6
subnet 255.255.255.0

linux box
192.168.1.17 the mask is the same

---

### Post by tfrue on 2014-02-11
So what exactly are you trying to do? Share? Monitor your network? ...

Chris

---

### Post by techanimelover on 2014-02-11
share files between my xp and linux boxs

---

### Post by tfrue on 2014-02-12
Have you defined any shares on Windows or Linux?

---

### Post by techanimelover on 2014-02-12
> **tfrue said:**
> Have you defined any shares on Windows or Linux?

Yes i have
would the fire wall on windows 7 block the Linux computer from seeing it?
i installed Samba but it would not launch

---

### Post by tfrue on 2014-02-12
So are you trying to share folders from both machines to each other? Did you use the GUI to share files from Linux?

---

### Post by bab1 on 2014-02-12
> **techanimelover said:**
> Yes i have
would the fire wall on windows 7 block the Linux computer from seeing it?
i installed Samba but it would not launch
Let's diagnose what you've got.  Post the output of these commands from the CLI of the Samba server```

pgrep -l mbd

testparm -s 

net usershare info --long

```

This will tell us[LIST]
[*]Whether the Samba server is running or not
[*]What the Samba Server configuration is 
[*]What Samba usershares you may have created
[*]
[/LIST]

---

### Post by techanimelover on 2014-02-16
i can see the Windows 7 machine now (knock on wood)
but windows 7 cant see the linux box which is now Lubuntu

---

### Post by deadflowr on 2014-02-16
> **techanimelover said:**
> i can see the Windows 7 machine now (knock on wood)
but windows 7 cant see the linux box which is now Lubuntu

Was this a lubuntu reinstall?

If so, have you reinstall samba?

---

### Post by techanimelover on 2014-02-16
i am working under a freash install of Lubuntu Samba is installed 
but now my wireless network adatpter has decided to give problems
if i unplug it and plug it back in it works for a minute or 2 then stops even though it says its connected

---

### Post by techanimelover on 2014-02-24
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = PAVILLIONPC
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Public]
    path = /home/thomas/Public
    read only = No
    guest ok = Yes

---

### Post by bab1 on 2014-02-24
> **techanimelover said:**
> ```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = PAVILLIONPC
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Public]
    path = /home/thomas/Public
    read only = No
    guest ok = Yes
```

What about the other 2 questions?  in addition post the output of this```
smbtree -d3
```

Place the output between the code blocks using the [SIZE=4]**#**[/SIZE] icon at the top of the reply editor.

---

### Post by techanimelover on 2014-02-25
what 2 other questions?
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The security=share option is deprecated
added interface wlan1 ip=fe80::ca3a:35ff:fec2:ae8%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface wlan1 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Enter thomas's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
Connecting to host=THOMAS-PAVILION
Connecting to 192.168.1.4 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED


```

---

### Post by bab1 on 2014-02-26
> **techanimelover said:**
> what 2 other questions?
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The security=share option is deprecated
added interface wlan1 ip=fe80::ca3a:35ff:fec2:ae8%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface wlan1 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Enter thomas's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
Connecting to host=THOMAS-PAVILION
Connecting to 192.168.1.4 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED


```

Upon reflection, it's the following 3 questions listed below.


Post the output of these commands from the CLI of the Samba server

```
pgrep -l mbd

testparm -s 

net usershare info --long
```

I see one error in the above output.  You have set the *security to share level *and this means that the login authentication is incorrect.  
Did you mean to use:    [FONT=Courier New]security=share[/FONT] for some reason?

---

### Post by techanimelover on 2014-02-26
i am a newbie setting this up
```
it_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Public]
    path = /home/thomas/Public
    read only = No
    guest ok = Yes


```

---

