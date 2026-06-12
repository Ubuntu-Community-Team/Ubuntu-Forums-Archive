---
title: "Windows Share Problems :("
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by nOmArch on 2007-10-27
Hi Guys,

after going through just about every samba howto on getting windows and ubuntu to talk to each other i've finally given up and admitted defeat. :(

Ubuntu Pc = 7.10 , Windows PC = XP SP2

i've just tried out this howto [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

and got somewhat further that any other attempt.

my problem is that when i double click on my ubuntu machine in the windows workgroup from my windows pc.  i get a login window where i enter my userid and password as setup from the howto. soon as i hit return it tells me that i cant log in because the account has been disabled.

i've searched everywhere in smb.conf and in the gsamba frontend but cant find anything that might be causing the problems.

heres my config file, hopefully you guys can work out where im being dumb.

[global]
    ; General server settings
    netbios name = Warrick	
    server string =Ubuntu
    workgroup = ORYX-NOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = nomarch	
    force group = nomarch
available = yes
browsable = yes
public = yes
writable = yes

---------

other than this damn networking issue im absolutely loving ubuntu :)

---

### Post by arsenic23 on 2007-10-27
hmmm....   In my experience Samba has always just worked after instal and minor tweak.  I've never tried to use a how-to to intall it.  It could be that the how-tos you've been trying are way out of date.  Here's a smb.cconf file based off mine if you'd like to try it.

```

[global]
workgroup = ORYX-NOME
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
socket options = TCP_NODELAY
wins support = no

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

[MyFiles]
path = /home/samba
available = yes
browsable = yes
public = yes
writable = yes

```

Just back up your currant smb.conf, replace it with this one, and restart your samba service with:
```
sudo /etc/init.d/samba restart
```

If it doesn't work you may want to just remove your samba config files, and remove/reinstall samba. -- or just wait for someone with a little more samba experience to drop by.

---

### Post by nOmArch on 2007-10-27
Hiya, Thanks for getting back to me!  will have a go with your config tonight. i also think that  may have been making this more complicated than it needs to be :)

---

### Post by mpince on 2007-10-28
> [MyFiles]
path = /home/samba
available = yes
**[COLOR="Red"]browsable[/COLOR]** = yes
public = yes
writable = yes


Why is  'browseable' spelled differently in this particular entry? All other entries in the smb.conf file have  with an 'e'? Is that the way it is supposed to be?

It's like that on my machine too. When I right click on a folder to start sharing a folder, ubuntu creates an entry in the Smb.conf file. It is always misspelled.

---

