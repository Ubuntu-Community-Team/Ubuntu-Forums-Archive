---
title: "Windows Networking"
date: 2005-06-26
forum: Networking &amp; Wireless
---

### Post by raghav_p on 2005-06-26
First, I have just about everything set up on Ubuntu and I love it. I soon plan to get rid of WinXP and just boot into Ubuntu. But first, I NEED to have Windows Networking set up. For that, I followed the "Unofficial Ubuntu Starter Guide" for changing workgroup. When I type sudo testparm, i get the following error:

raghav@TRINITROTUOLENE:~$  sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = PURANMALKA
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

Nonetheless, I can access the Windows shares on other computers but cannot view my computer in the work group. Can any one help??

---

### Post by wylfing on 2005-06-26
I think you should set browseable=yes in order to see the shares in the network browser. Try hopping on a Windows machine and entering the address of a share directly (Start > My Network Place > Add a network place, when asked for the address type \\machinename\sharename). If that works, then your problem is simply that you can't "browse" to the shares.

---

### Post by desdinova on 2005-06-26
[www.samba.org](www.samba.org) has an excellent write up on Samba with some good howto's on setting it up.

---

### Post by raghav_p on 2005-06-26
Sorry..

I just realized I didn't install Samba.. god.. Im a stupid n00b... :mad: 

I heart Ubuntu  :)

---

