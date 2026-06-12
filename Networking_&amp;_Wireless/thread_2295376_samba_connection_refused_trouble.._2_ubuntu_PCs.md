---
title: "samba connection refused trouble.. 2 ubuntu PCs"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by Haki_Red on 2015-09-18
Hello all,

So I'm trying to get 2 Ubuntu 15.04 PCs to share files with each other via samba.
They both have the same **smb.conf **file.
However samba is acting strange

Here is how it works right now if i do smb://Adress via **Nautilus'** *Connect To Server*
PC1 -> PC1 = works (both clicking the icon in Browse Network or manually connecting to it via smb://192.168.0.123/ Connect To Server
PC1 -> PC2 = works
PC2 -> PC2 = works
PC2 -> PC1 = does not work. I get "connection refused" if i click on the icon via Browse Network, 
                        Or i get "connection timed out" if i tyoe smb://192.168.0.123/ via Connect to a Server in nautilus

Setup:
PC1 connected via WIFI with static IP : 192.168.0.123
PC2 connected via WIFI and ETHERNET with static IP: 192.168.0.122

Bother computers have the same usernames : hakired but different computer names

**here is the smb.conf**

```

#======================= Global Settings =======================


[global]
   workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
   dns proxy = no
   usershare owner only = false


#### Networking ####


#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
   server role = standalone server  
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user


########## Domains ###########




############ Misc ############


   usershare allow guests = yes


#======================= Share Definitions =======================


[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   read only = no


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


[print$]
   comment = Printer Driver
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

# ============== END OF FILE ==========

```

I've been googling for hours on end right now but none of the solutions worked.

Even the default smb.conf file will produce the same error,
Ive tried purging, removing, reinstalling.

pretty much what I do after each fresh install of samba is just do
sudo smbpasswrd -a hakired

---

### Post by Haki_Red on 2015-09-18
Okay apparently same thing is happening with vsftp PC1 is not accesible by anyone else but itself PC2 however is accesible by PC1

---

### Post by Bucky Ball on 2015-09-18
*Thread moved to **Networking & Wireless**.*

Welcome. Can you ping all machines from each other? E.g. if the IP address of machine 1 is 192.168.0.200, can you open a terminal on machine 2 and:

```
ping 192.168.0.200
```

? Can you also go the other way? Can you ping the machine you are having issues with from the one that you're not?

Have you got static IP addresses or you are communicating, or trying to, by machine name?

PS: Please see the last link in my signature and use code tags for terminal output. Thanks. :)

---

### Post by Haki_Red on 2015-09-18
Yes I'm able to ping 192.168.0.123 (PC1) From all PCs, 

Additional info: 
I've added another laptop PC3 running Lubuntu and is able to ftp and smb with PC2 just fine. It seems to me that PC1 is just refusing any connection whether it be FTP  or SMB, tho the service is running correctly
because i can FTP to PC1 from PC1. 

And yes they are all set to have static IP. 
I'm 1 step away from just reinstalling Ubuntu on it :(

---

### Post by Haki_Red on 2015-09-18
Gave up in the end had to reinstall ubuntu and it works flawlessly. I must have indirectly messed it up tinkering with other stuff, One thing I can think of on the top of my head was I died a lot of trial and error setting up an SSH server on PC1 messed up with alot of settings with that one. Sorry to those that would encounter the same problem in the future.

---

### Post by Bucky Ball on 2015-09-18
All good. In the absence of a 'resolved' option could you see the first link in my signature to help others and mark thread as 'solved', please? Thanks.

Enjoy the forums and the OS. :)

---

