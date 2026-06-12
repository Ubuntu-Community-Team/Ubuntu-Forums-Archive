---
title: "how to make windows client to browse files in ubuntu server?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by buntubayoe on 2007-11-02
hello, :KS
how to make windows client to browse file in ubuntu server?
we setting up with bridge connection between eth0 and eth1, eth0 is internet side with asdl type and eth1 is windows based client. the client computer can connect the internet.
and 
we have been installing samba-doc. the program is bellow:

apt-get install samba   samba-doc
etc....

[global]
workgroup = belkin
server string = % server (samba %v)
log file = /var/log/samba/log.%m
max  log size = 1000
sylog = 0

security = share

encrypt paswords = true

passdb backend = tdbsam guest

guest account = nobody

invalid users = roots

passwd program = /usr/bin/passwd %u
passwd chat = *enter\snew\sUNIX\spassword:* %n\n
*retype\snew\sUNIX\spassword:*%n\n .

[shared]
  comment = shared folder
  path = /windows
 browsable = yes
 guest ok = yes

our client can browse ubuntu server but when i click the windows folder that is in ubuntu server (windows folder is the name of our shared folder' in ubuntu server) it cannot be accessed...(network access is denied). but i can click printers and fax folder in ubuntu server without network acces is denied.

we are using ubuntu 7.10
with windows home edition in client side

could anyone give me a hand to solve these problem :confused: :confused:

---

### Post by JayvJay on 2007-11-04
Is samba installed and started on linux.  Did you give it a password?

---

### Post by infinitezero on 2007-11-05
Check out this link, download the howto pdf, hope it helps.

[http://ubuntuforums.org/showthread.php?t=575214](http://ubuntuforums.org/showthread.php?t=575214)

iz

---

