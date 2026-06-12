---
title: "samba/winbind problem in Hardy"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Charlotte18 on 2008-05-31
I'm at my wit's end, so maybe someone can help. First, I cannot use Likewise, so it's no use to suggest that. (In case you're wondering, I need users to be able to logon to their usernames without typing the domain and separator and without my mapping them all.) Second, the problem below only happens in Hardy, not in Gutsy, even though I'm configuring things the same. In fact, if I do a fresh install of Gutsy and upgrade to Hardy, there are no problems.  So . . .

On a fresh install of Hardy, I can install krb5 and get a ticket for the AD admin in Windows 2003 Server. I can install samba and winbind, set up the appropriate files in the etc folder, and join the Hardy box to the network with no problem. I can logon as a normal user in AD.  Then, as the Hardy desktop is about to come up, I get a "Your session only lasted 10 seconds" error, and the error log shows that a number of processes or applications (e.g., seahorse) "failed due to unknown user id" or "could not get password database information for UID of current process."  There are several "500" errors like this labeled "getpwuid_r()."  Then, I'm back to the logon screen. I can only reach the desktop with a local user account, but it appears the AD accounts are authenticating but getting bumped quickly because of these errors. It seems as if some credentials on the local box are not getting set properly, but I don't know how to approach this problem.

My nsswitch.conf file looks like this:
[INDENT]passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis[/INDENT]

Any ideas?

---

### Post by dmizer on 2008-05-31
put wins in front of dns like so:
```
passwd: compat winbind
group: compat winbind
shadow: compat

hosts: files [COLOR="Red"]wins[/COLOR] dns
networks: files

protocols: db files
services: db files
ethers: db files
rpc: db files

netgroup: nis
```

this will cause wins to be resolved before dns, and may fix your problem.

---

### Post by Charlotte18 on 2008-06-02
Unfortunately, that simple change to nsswitch.conf didn't stop the error. The "failed due to unknown user ID" errors that I described above still occur with various processes (seahorse-agent, for example). The logon appears successful. The 'home' folder is created. The desktop won't come up because of the errors, though, and the user is bumped back to the logon screen after "okaying" the errors.

---

