---
title: "Unable to run Samba"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by philipwmirabelli on 2016-05-14
Hello, I have installed and reinstalled Samba but I come up with the same issue.  I am running Kubuntu 16.04 LTS with Plasma 5.5.5 and want to use my linux box as a server creating a shared file for my windows machine to see and add/remove files.  I cannot get the config samba GUI to open, the Samba icon is in  the main menu but when I click on it I do get the dialog box asking for my password, after inserting the password - nothing.....I have tried issuing "testparm" command and I get the following:

[COLOR=#ff0000]"Load smb config files from /etc/samba/smb.conf[/COLOR][COLOR=#ff0000]rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)[/COLOR]
[COLOR=#ff0000]WARNING: The "syslog" option is deprecated[/COLOR]
[COLOR=#ff0000]Processing section "[printers]"[/COLOR]
[COLOR=#ff0000]Processing section "[print$]"[/COLOR]
[COLOR=#ff0000]Processing section "[share]"[/COLOR]
[COLOR=#ff0000]Loaded services file OK.[/COLOR]
[COLOR=#ff0000]WARNING: The 'netbios name' is too long (max. 15 chars).[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Server role: ROLE_STANDALONE[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Press enter to see a dump of your service definitions[/COLOR]

[COLOR=#ff0000]# Global parameters[/COLOR]
[COLOR=#ff0000][global][/COLOR]
[COLOR=#ff0000]    workgroup = HOME[/COLOR]
[COLOR=#ff0000]    server string = samba server %v server (Samba, Ubuntu)[/COLOR]
[COLOR=#ff0000]    server role = standalone server[/COLOR]
[COLOR=#ff0000]    map to guest = Bad User[/COLOR]
[COLOR=#ff0000]    obey pam restrictions = Yes[/COLOR]
[COLOR=#ff0000]    pam password change = Yes[/COLOR]
[COLOR=#ff0000]    passwd program = /usr/bin/passwd %u[/COLOR]
[COLOR=#ff0000]    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/COLOR]
[COLOR=#ff0000]    unix password sync = Yes[/COLOR]
[COLOR=#ff0000]    syslog = 0[/COLOR]
[COLOR=#ff0000]    log file = /var/log/samba/log.%m[/COLOR]
[COLOR=#ff0000]    max log size = 1000[/COLOR]
[COLOR=#ff0000]    dns proxy = No[/COLOR]
[COLOR=#ff0000]    usershare allow guests = Yes[/COLOR]
[COLOR=#ff0000]    panic action = /usr/share/samba/panic-action %d[/COLOR]
[COLOR=#ff0000]    idmap config * : backend = tdb[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000][printers][/COLOR]
[COLOR=#ff0000]    comment = All Printers[/COLOR]
[COLOR=#ff0000]    path = /var/spool/samba[/COLOR]
[COLOR=#ff0000]    create mask = 0700[/COLOR]
[COLOR=#ff0000]    printable = Yes[/COLOR]
[COLOR=#ff0000]    browseable = No[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000][print$][/COLOR]
[COLOR=#ff0000]    comment = Printer Drivers[/COLOR]
[COLOR=#ff0000]    path = /var/lib/samba/printers[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000][share][/COLOR]
[COLOR=#ff0000]    comment = Ubuntu File Server Share[/COLOR]
[COLOR=#ff0000]    path = /srv/samba/share[/COLOR]
[COLOR=#ff0000]    read only = No[/COLOR]
[COLOR=#ff0000]    create mask = 0755[/COLOR]
[COLOR=#ff0000]    guest ok = Yes"

[/COLOR]does anyone have any idea how I can get the config GUI of Samba working??

thanks [COLOR=#ff0000]
[/COLOR]

---

