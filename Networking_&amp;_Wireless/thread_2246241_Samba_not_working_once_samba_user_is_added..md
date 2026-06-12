---
title: "Samba not working once samba user is added."
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by mmans2 on 2014-09-29
Samba doesn't work once I add any user. Having no users (but just a guest account) works fine. 

smb.conf
```

[global]
  workgroup = WORKGROUP
  netbios name = vpn

  security = user
  map to guest = Bad User
  guest account = samba

[home]
  path = /home/%U
  guest ok = no
  writable = yes

[share1]
  path = /storage/share
  guest only = yes
  writable = yes

```

When I have no users (deleted them all), I can access share1 just fine. When I try to access the home share it prompts me for a password, which seems normal to me since it allows no guests.
Now I add  a new user and restart the service:
```

adduser user
smbpasswd -a user
service smbd restart

```
All goes fine, I get no errors etc...

When I now try to access share1 or home it prompts me for a password, but entering the correct password and username returns "Windows cannot access \\10.0.0.1\share1". Entering a wrong password also gives the same message. When I try to access \\10.0.0.1 it also prompts for a password and I get the error ""\\10.0.0.1 is not accessible. You might not have permission to use this network resource".

Removing the user with ```
smbpasswd -x user
``` and reloading smbd turns everything back to "normal".

These samba shares can only be accessed over a vpn connection (pptp). My understanding is that Windows automatically tries to use the same credentials used for the vpn (I guessed wrong, this does not happen), on shares in that network. If that fails, windows prompts for other credentials. This way I try to achieve seemingly passwordless samba shares (and a 'home' share that is unique for every vpn login). 

Some additional information:
Ubuntu 14.04.1 / Windows 7
Samba Version 4.1.6-Ubuntu
```
C:\Windows\system32>net use * /DELETE
There are no entries in the list.
```

---

### Post by bab1 on 2014-09-29
> **mmans2 said:**
> Samba doesn't work once I add any user. Having no users (but just a guest account) works fine. 

smb.conf
```

[global]
  workgroup = WORKGROUP
  netbios name = vpn

  security = user
  map to guest = Bad User
  guest account = samba

[home]
  path = /home/%U
  guest ok = no
  writable = yes

[share1]
  path = /storage/share
  guest only = yes
  writable = yes

```

When I have no users (deleted them all), I can access share1 just fine. When I try to access the home share it prompts me for a password, which seems normal to me since it allows no guests.
Now I add  a new user and restart the service:
```

adduser user
smbpasswd -a user
service smbd restart

```
All goes fine, I get no errors etc...

When I now try to access share1 or home it prompts me for a password, but entering the correct password and username returns "Windows cannot access \\10.0.0.1\share1". Entering a wrong password also gives the same message. When I try to access \\10.0.0.1 it also prompts for a password and I get the error ""\\10.0.0.1 is not accessible. You might not have permission to use this network resource".

Removing the user with ```
smbpasswd -x user
``` and reloading smbd turns everything back to "normal".

These samba shares can only be accessed over a vpn connection (pptp). My understanding is that Windows automatically tries to use the same credentials used for the vpn, on shares in that network. If that fails, windows prompts for other credentials. This way I try to achieve seemingly passwordless samba shares (and a 'home' share that is unique for every vpn login). 

Some additional information:
Ubuntu 14.04.1 / Windows 7
Samba Version 4.1.6-Ubuntu
```
C:\Windows\system32>net use * /DELETE
There are no entries in the list.
```

For Samba to to work correctly you need to have both a Linux (Ubuntu) account and a samba user (smbpasswd).  

In addition the correct name for the private share should be  [homes].

---

### Post by mmans2 on 2014-09-29
All I had to do was 
```
/etc/init.d/nmbd restart
```
:-|

nmbd cannot be restarted with "service nmbd restart", which I tried before.

---

### Post by bab1 on 2014-09-29
> **mmans2 said:**
> All I had to do was 
```
/etc/init.d/nmbd restart
```
:-|

nmbd cannot be restarted with "service nmbd restart", which I tried before.  

The daemon *nmbd * is for netbios name resolution.  It has nothing to do with users.

The *nmbd* daemon most certainly can be started by the incantation "sudo service nmbd restart".  It needs sudo as only root can restart the daemon.  here is my output to the response```
sudo service nmbd restart
[sudo] password for bab: 
nmbd stop/waiting
nmbd start/running, process 3200

``` In fact you must be root to restart the daemon using "/etc/init.d/nmbd restart" also.  If you are not root here is what you get```
 /etc/init.d/nmbd restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service nmbd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop nmbd ; start nmbd. The restart(8) utility is also available.
[COLOR="#FF0000"]stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.76" (uid=1000 pid=3221 comm="stop nmbd ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")[/COLOR]

```
Note the red portion above shows what happens when you fail to use sudo or are root.

None of this has anything to do with user authentication.  It may have to do with locating the SMB resource.  Did you reboot the system?  That would account for why you can now use the shares.

As you solved the problem the please **mark the thread solved** so that others following this will know that.

---

