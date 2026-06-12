---
title: "LDAP configuration issues - boot lockup or no LDAP groups"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by dorsey on 2008-07-22
I have a series of systems running Hardy that authenticate against LDAP.  I have an issue with finding LDAP groups and getting the system to boot.

My current /etc/nsswitch.conf looks like this:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns ldap
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       ldap

```

If I keep it like that, the machine boots properly, but my LDAP group containing sudo users doesn't have an effect until I run 'groups'.  I guess then it actually searches the groups and lets me sudo properly.

If I change that to
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         ldap files
group:          ldap files
shadow:         ldap files

hosts:          files dns ldap
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       ldap

```

The groups show up properly immediately (sudo works without first running groups') but when I reboot, the machine locks on "Starting kernel event manager..."

Does anyone have any tips on how I can make this work properly?  I'd prefer to fix the boot issue, but no other workaround will let me boot, including adding "bind_policy soft" to /etc/ldap.conf.

---

### Post by argail1980 on 2008-07-22
I had this system-lock bug from the start. maybe my solution helps, but I'm not sure.

I changed the boot order, because some service was hanging when waiting for LDAP to start.
you change the boot order by renaming the links in ```
/etc/rc2.d
```
change the number at the start of the slapd entry (in my case S19slapd) to something that is smaller that the others, in my case S09slapd

```
mv /etc/rc2.d/S19slapd /etc/rc2.d/S09slapd
```

---

### Post by dorsey on 2008-07-22
> **argail1980 said:**
> I had this system-lock bug from the start. maybe my solution helps, but I'm not sure.

I changed the boot order, because some service was hanging when waiting for LDAP to start.
you change the boot order by renaming the links in ```
/etc/rc2.d
```
change the number at the start of the slapd entry (in my case S19slapd) to something that is smaller that the others, in my case S09slapd

```
mv /etc/rc2.d/S19slapd /etc/rc2.d/S09slapd
```

That would work for the server, but this machine is just one of the clients.  There's no slapd init file on it.

---

### Post by argail1980 on 2008-07-22
ok, I see. 
unfortunately I have only windows clients for now. Sorry I could not help.

btw, here is my /etc/nsswitch.conf on the server, maybe you can use something there

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: compat ldap
group: compat ldap
shadow: compat ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by dorsey on 2008-07-23
> **argail1980 said:**
> ok, I see. 
unfortunately I have only windows clients for now. Sorry I could not help.

btw, here is my /etc/nsswitch.conf on the server, maybe you can use something there

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: compat ldap
group: compat ldap
shadow: compat ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

I changed my "files ldap" section to match your "compat ldap", thinking that might have a change; sadly it didn't.  Thanks for the help, though; I guess I'll just get used to typing 'groups' before I sudo from now on :-D

---

### Post by dorsey on 2008-07-23
Actually, I'm an idiot.  There's a specific package 'sudo-ldap' that I need to use instead of standard sudo.  Now that this version of sudo is installed, I should have no problems.  Thanks for all your help though!

---

