---
title: "Samba has failed me"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2006-09-12
i need my dapper notebook (daniel-laptop) to be able to access my windows desktop (computer name: FAMILY, workgroup: bolton)

i've read thread 202605 several times. i'm pretty sure that i have samba configured properly:

```

[global]
    ; General server settings
    netbios name = FAMILY
    
    workgroup = BOLTON
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

 ;Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /network
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes


[SharedDocs]
path = /home/network
available = yes
browseable = yes
public = yes
writable = yes

[SHARED]
path = /home/daniel/SHARED
available = yes
browseable = yes
public = yes
writable = yes


```

i go to Places-> Connect to Server, then choose Windows share. if i type "FAMILY" or "family" for the "Server" attribute, the server only displays shared folders on the dapper notebook. "\\family" doesn't work. 

if i type in the desktop's IP as "server" attribute, i get a password prompt: "You must log in to access [email]guest@192.xxx.xxx.xxx[/email]", which asks for user, domain, and password. by default, the user field says "daniel" and the domain field says "WORKGROUP".

on both computers, i have this account:
username= daniel
password= XXXXXX

i have tried just entering the password, leaving everything blank, leaving all fields blank and typing "guest" as username, changing "WORKGROUP" to "bolton" (the windows desktop's workgroup) and entering "daniel" and "XXXXXX", et cetera. nothing seems to work.

i added user "family" and user "guest" on the dapper box, as well as to samba using the terminal [sudo smbpasswd -e family], and added user "family" to grop "family" according to one thread that i read.

on the windows computer, i try this:
go to My Network Places-> Add Network Place

in the field, i enter things like "\\daniel-laptop\daniel\shared", this prompts for username and password- but the user field is locked as "\\FAMILY\guest"! of course i can't make that user on the linux due to the "\" character. entering password "xxxxxx" doesnt work.

i am very lost. i think i will have to totally erase samba and all shared folders and start again. any help is much appreciated.

-daniel

---

### Post by tbonius on 2006-09-12
Do you need passwords on the shares?  If you do .. make sure that you use smbpasswd to add users and passwords to samba.  If you do no need usernames and passwords for the shares.. simplify your life.. something like:

```
# Global parameters
[global]
        workgroup = BOLTON
        server string = FAMILY
        security = SHARE
        preferred master = No
        local master = No
        domain master = No
        printing = CUPS
        printcap name = CUPS

[Share]
        path = /example/share
        read only = No
        guest ok = Yes

```

Be sure and chmod 777 the directory to open it up for everyone (if you dont want to lock it down)

T

---

### Post by Iowan on 2006-09-12
> i need my dapper notebook (daniel-laptop) to be able to access my windows desktop (computer name: FAMILY, workgroup: bolton)
The Windows machine is named FAMILY?  If your Samba config is on the notebook, it has made the notebook name FAMILY.  The smb.config generally sets up a server.  If you want to access files FROM whe Windows box, you need the Samba client software (I didn't need to install it when I set up my workstation).

Try changing the line:```
netbios name = FAMILY
``` to
```
netbios name = daniel-laptop
```

---

### Post by dbbolton on 2006-09-12
thank you both.

i am going to play around with this and see if it works

---

### Post by Iowan on 2006-09-12
More a matter of "when" than "if"... :wink:

---

### Post by dbbolton on 2006-09-13
is there some way that on windows i can "add a network place" such as:

```
smb://daniel:XXXXXX@daniel-laptop/home/daniel/shared
```

---

### Post by Iowan on 2006-09-13
Yes, under "Add Network Place" the "Browse" button should list "daniel-laptop" as a machine (assuming the workgroup is the same on both machines).  Might also be visible under "View Workgroup Computers".  Depending on how Samba has the share mapped, it might just be:
\\daniel-laptop\daniel\shared
or... something completely different.

---

### Post by dbbolton on 2006-09-13
i completely re-made my samba config, users, passwords, etc and followed thread [202605]("http://www.ubuntuforums.org/showthread.php?t=202605") to the T.

now, windows says that "\\daniel-laptop\home\samba\" doesn't exist. (i changed the shared folder according to the thread)

the IP's given by WiFi Radar, system-> admin-> network-> hosts-> "daniel-laptop", and system-> admin-> network-> wireless connection-> properties are all different. which one do i put for the WINS in the windows desktop?


thanks again.

---

### Post by Iowan on 2006-09-13
Which way did you end up:
```
path = /home/samba/
```
or
```
path = /media/samba/
```
Can Windows find just \\daniel-laptop (or \\daniel-laptop\MyFiles - or whatever you called it)?

If I read your reference thread correctly, the WINS address would be whatever static address you assigned to your laptop (assuming the laptop is set to act as WINS server) - especially if you:
```
    interfaces = lo, eth0
    bind interfaces only = true
```
> 
Now only the local loopback interface (dubbed "lo") and eth0 are able to access samba - there's no need to fear that someone might break into your system by wireless as the interface isn't bound to the service.

---

### Post by dbbolton on 2006-09-14
i don't think i can do that- i connect to the internet through eth1. if one can't do this through eth1, would it be possible to set up the network place by hardwiring the laptop to the wireless router?


here's my new smb.conf:


```
[global]
    ; General server settings
    netbios name = daniel-laptop
    server string =daniel-laptop
    workgroup = BOLTON
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
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel
available = no
public = no
writable = no

[samba]
path = /home/samba
comment = shared files
available = yes
browseable = yes
public = yes
writable = yes

```

my static ip is 203.258.100.XXX (i think this actually my wireless router's address) while "localhost daniel-laptop" is 127.0.1.XXX and the wifi radar says the ip is 192.168.1.XXX

i put all three on the WINS list- 192.168.1.XXX at the top. i noticed a check-box there that mentioned some sort of look-up. it was checked by default, but the guide didnt say anything about it. should it be checked ?

---

### Post by tbonius on 2006-09-14
Do you have a WINS server?  If not then remove the option.  Augment the file I posted earlier.  Do you need users and passwords for the shares?  If not augment the file I posted earlier.  Do you need Samba to be Master Broswer or announce its OS version for the network?  If not then augment the file I posted earlier. 

You have two shares listed with the same path:

MyFiles and Samba

Both point to the /home/samba directory which will be shared as each of those shares.  Do you need that?  Try to connect remotely to just the IP of the Ubuntu machine (\\192.168.x.x  -or- smb://192.168.x.x from Linux).  Can you see the shares?

A lot of Samba options are nice.. but not needed in a home networking environment.  You will save yourself so much headache if you start with a simple smb.conf file.

T

---

### Post by dbbolton on 2006-09-16
i'm not sure how, but it works now. i ran synaptics updatemanager, restarted, and then got on my windows desktop. it turns out that i had to enter ```
\\daniel-laptop\samba
``` in lieu of ```
\\daniel-laptop\home\samba
``` in "add network place". this seems odd to me, considering that the actual folder is located at ```
/home/samba
```

anyhow, i verily appreciate all the help.

one last question:
how would i connect to the share 
```
\\family\shareddocs

which is

C:\Documents and Settings\All Users\SharedDocs
``` from my linux box through Places>Connect to server? here is what i have tried there (commas separating different combos, etc):
```

service type: windows share
server: family, 192.168.1.xxx, \\family, 208.253.100.xxx
----------
share:shareddocs, C:\documents and settings\all users\shareddocs,
folder:
username: (leave blank), daniel,
domain: (leave blank), bolton,
name to use for connection: whatever

```

either just the samba folder will show up, or else i will get an error message.


thanks again.

---

