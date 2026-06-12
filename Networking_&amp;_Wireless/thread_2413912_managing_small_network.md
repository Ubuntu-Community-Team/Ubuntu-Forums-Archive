---
title: "managing small network"
date: 2019-03-03
forum: Networking &amp; Wireless
---

### Post by philbar12 on 2019-03-03
Help Please!!!
I have Ubuntu 18.04 Bionic Beaver and I would like to turn it into 
a Samba PDC in order to manage my small network.
I've been able to create a primary domain controller by following the
Samba HOW TO docs for version 3, but I have Samba 4 and I'm not sure
if these configurations still apply.
I've been able to join clients (Ubuntu 18.04) to the domain but I have
not been able to login to the client using domain credentials.  The login
screen will automatically create an entry for the domain user but show 
that the password is invalid.  To explain a bit more, when a valid domain
user account is used to attempt to logon, e.g., "RABBITS\tom", the greeter
will add that name to the list of names it displays as having accounts on
the machine.  But, if I use an invalid account in an attempt to login,
it will not add it to the greeter screen leading me to believe that
validation is actually occurring but something else is not happening.
So what I'm asking is this: 
 How do I create an NT-4 style Samba primary domain controller?
 Does anyone have a working example I could use?
 
 How do I join a client machine to this domain?
 Does anyone have a working example of a domain member config to use?
 How do I login to this client machine using domain credentials?
 Could someone please walk me through this line by line?
 Are there any resources available that you can point me to that
 address these concerns?
Thanks for any help!
THIS IS THE smb.conf for the domain controller named "3rabbit"
```

####################################
[global]
    workgroup = RABBITS
 netbios name = 3rabbbit
 security = user
 passdb backend = tdbsam
 encrypt passwords = yes
 obey pam restrictions = yes
 os level = 33
 preferred master = yes
 domain master = yes
 local master = yes
 domain logons = yes
    add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u 
 server string = %h server (Samba, Ubuntu)
    wins support = yes
    dns proxy = no
    bind interfaces only = yes
    log file = /var/log/samba/log.%m
    max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
#The parameter 'server role' was changed to this and commented out by Samba
;when I promoted it to the PDC using 'net rpc join PDC' command after having
;run 'net rpc join MEMBER' command.
;   server role = class primary domain controller
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
########## Domains ###########
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   usershare allow guests = yes
[netlogon]
 comment = Network Logon Service
 path = /home/samba/netlogon
 guest ok = yes
 read only = yes
[public]
 comment = This is a public test share
 path = /home/samba/public
 read only = yes
 guest ok = no
 valid users = 2rabbit\cbinch
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
##############END OF FILE####################################
What follows is the smb.conf file for my domain member machine which has a machine
account on the domain controller.
###########################################

[global]
 

 workgroup = RABBITS
 wins server = 10.0.0.1
 server role = member server
 security = domain
 null passwords = yes
 map to guest = bad uid
 server string = %h server (Samba, Ubuntu)
   dns proxy = no
   bind interfaces only = yes
 
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   passdb backend = tdbsam
   encrypt passwords = yes
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad uid

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   usershare allow guests = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
##################END OF FILE####################################
```

---

### Post by QIII on 2019-03-03
Hello!

Please include all terminal commands and their output, as well as the contents of config files and such, in code tags.  That will preserve formatting and make your posts easier to read.

To use code tags, either:

1:  Click the # button in the toolbars above the text entry area, place your cursor between the code tags that appear, then type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2:  Type [noparse]```
[/noparse] before the text and [noparse]
```[/noparse] after it.  The square brackets are required.

Cheers!

---

