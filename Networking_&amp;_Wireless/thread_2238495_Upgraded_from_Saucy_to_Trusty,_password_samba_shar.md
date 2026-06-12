---
title: "Upgraded from Saucy to Trusty, password samba share stopped working"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by kripz on 2014-08-08
```
user@fileserver:/storage/$ smbclient \\\\192.168.1.134\\password$ -U user -d 4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter log level = 0
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server
doing parameter name resolve order = wins lmhosts host bcast
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter map to guest = bad user
doing parameter username map = /etc/samba/smbusers
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter create mask = 666
doing parameter force create mode = 666
doing parameter force directory mode = 0777
pm_process() returned Yes
added interface eth0 ip=192.168.1.134 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter user's password: 
Connecting to 192.168.1.134 at port 445
 session request ok
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
 session setup ok
tree connect failed: NT_STATUS_ACCESS_DENIED

```

I am running that command locally on the file server, it's IP address is 192.168.1.134.

Entering the wrong password gives me 

```
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
```

None of my 14.04 machines can access it, previously the samba server was running 13.10 (IIRC) and had no issues.

---

### Post by kripz on 2014-08-09
help

---

### Post by kripz on 2014-08-10
```
sudo apt-get remove samba
sudo aptitude install -t saucy samba
```

Let aptitude fix dependancy downgrades, removed registry.tdb, started samba:

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.18]
 session setup ok
 tconx ok
```

Nothing else was changed.

Something broken in samba4.

---

