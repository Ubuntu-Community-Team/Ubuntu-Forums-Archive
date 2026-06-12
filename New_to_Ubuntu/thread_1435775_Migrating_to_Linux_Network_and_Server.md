---
title: "Migrating to Linux Network and Server"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by LWhitson2 on 2010-03-21
Ok, I am still fairly new to this whole Linux thing, but I am really liking everything so far.  I would like to start migrating my home network over to Linux, but I am really overwhelmed at how to make that happen.  The network I currently have is pretty stable, but is lacking in a lot of ways because I don't have the money to pour into MS products.  Here is the network infrastructure I would like to set-up in Linux.  What I am really looking for is some kind of road-map to make this happen as well as any good resources to teach me how to do each of these things.

Networking Goal:

2 Servers: one Domain Controller / Credential Store / File Server, one Website Host with PHP and MySQL at least

Linux Workstations: Ability to sign on all workstations with single user name and password, preserving Home Drive etc... (Notebooks must be able to be used even when not on home network)

Windows Workstations: Same as Linux above, but with ability to mount Home drive as H: or similar (Again, Notebooks need to be used away from home)

Network Printers / Scanners: Multiple printers and scanners hooked to DC with ability to use on all machines

Alright, any thoughts or suggestions or where to start or how to do this?

---

### Post by jimv on 2010-03-25
Look into OpenLDAP and Samba (as a domain controller).  OpenLDAP handles the credentials and Samba does the profiles/storage.  There are some very good tutorials if you google a bit.

---

