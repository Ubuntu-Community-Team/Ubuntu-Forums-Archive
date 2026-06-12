---
title: "samba"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by serfczar on 2007-08-16
I am not able to write to the folder specified that I can write to, what's going on?



workgroup = WORKGROUP

server string - %h server (Samba, Ubuntu)

dns proxy = no

log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic action %d

encrypt passwords = true

passdb backend = tdbsam

obey pam restrictions = yes

invalid users = root

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword: * %n\n *Retype\snew\sUNIX\spassword:*%n\n *password\supdated\ssucessfully* .

socket option = TCP_NODELAY

[printers]

comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

[Iso Server]
writeable = yes
valid users = serfczar
user = serfczar
path = /iso
write list = serfczar

---

### Post by serfczar on 2007-08-16
SOLVED, had to chmod the folder to 777

---

