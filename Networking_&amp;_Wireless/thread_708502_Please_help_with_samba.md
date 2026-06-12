---
title: "Please help with samba"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by mr tim esquire on 2008-02-26
Please give me a hand with this samba setup, its a nightmare!
my /etc/samba/smb.conf is below
Im in Win XP trying to open a samba share thats on my ubuntu server.
the server(thefarm) is present in the domain(mousenet) but when i double click on the share(stuff) i get the following error.
```
\\Thefarm\stuff is not accessable.  You might not have permisson to use this network resourse.  
The user could name not be found
```
any ideas anone?
thanks!


```
[global]
    ; General server settings
    netbios name = thefarm
    server string =
    workgroup = mousenet
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

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

[stuff]
    path = /media/sdb1
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tim
    force group = tim

```

---

### Post by dca on 2008-02-26
Are you able to connect to it using the 'Map Network Drive' function in MSWinXP?  'Right-click' the Network folder and it should be there.
 
\\*IPAddressofServerorHostName*\stuff
 
...then select 'use different name' option and put in your credentials and see if you can get in that way...  Hmmm, if you can connect to it or not connect to it using that than I'm out of options...

---

### Post by mr tim esquire on 2008-02-26
When i try to map a network drive i get the error
 ```
an extended error has occured
```
sighhhhh...

---

### Post by Eiríkr on 2008-02-26
Hey there Tim --

Try opening an Explorer window and type just [font=courier]\\thefarm[/font] into the address bar.  If you can see your shares, then the problem is indeed with permissions on the shares themselves.  If just [font=courier]\\thefarm[/font] *also* generates an error, then we've got some other connectivity trouble in place.  

Given the error message you reported above, 
```
The user could name not be found
```
(I assume this should be "the user **name could** not be found"?)
the problem is likely that the username you have on your Win box is not being recognized on the Linux end of things.

The easiest setup is to have your Win and Lin usernames and passwords be identical.  If they aren't the same, you can run into issues like this one.  Rather than going to the bother of having to change your username(s), Samba supplies us with a handy way of mapping usernames from one system to the other -- the [font=courier]username map[/font] global option -- which you appear to be using.  

This suggests that your /etc/samba/smbusers file contains incorrect information.  Could you post the contents of this file, and let us know what your Win and Lin usernames are?  (Feel free to change them "to protect the innocent", as it were. :) )  I suspect that we can get you up and running if we can get this username mapping fixed.  

Cheers,

Eiríkr

---

