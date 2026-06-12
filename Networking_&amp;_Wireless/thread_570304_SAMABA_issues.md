---
title: "SAMABA issues"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by rabbit69ca on 2007-10-08
I am having issues in getting SAMBA working between too ubuntu machines (one lappy and one desktop)

Now the desktop can see the folder (and can view its contents) that I have shared on laptop, but occasionally I get that I do not have permissions to move files between the two. 

The laptop cannot see the folders that are shared on the desktop. saying that the contents cannot be displayed. 

Now I know samba is working because my modded xbox is able to access the desktop via SMB, but it cannot access the lappy.. 

here is the smb.conf from the laptop and I will post the smb.conf from the desktop on a second post once i get onto the desktop. 
```
 [global]
    ; General server settings
    netbios name = ian-laptop
    
    workgroup = NAKONECHNY
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
  ;  username map = /etc/samba/smbusers
  ; name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes


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
    path = /media/FILES/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ian	
    force group = ian

available = no
browsable = yes
public = no
writable = no

[FILES]
path = /media/FILES
comment = FILES
available = yes
browsable = yes
public = yes
writable = no

```


it should also be noted that there are 3 other machines on the network,  one is another ubuntu machine, that has samba running but has nothing of value to me, a windows machine that is in the same boat, and a modded xbox that allows me to watch videos off my comps on my TV. 

any assistance in this issue is greatly appreciated.

---

### Post by rabbit69ca on 2007-10-08
As promised the smb.conf from the desktop.

```
[global]

    netbios name = ianlinux

    server string = ianlinux

    workgroup = NAKONECHNY
    security = SHARE

   ;null passwords = true

   ;username map = /etc/samba/smbusers

    wins support = yes
    interfaces = lo, eth0

    bind interfaces only = true





[myfiles]

path = /media/hda4

available = yes
browsable = yes
public = yes
writable = yes


[ian]

        path = /home/ian

        username = ian

        valid users = ian

        admin users = ian

        read only = Yes

        only user = Yes

	available = no
	browsable = no
	public = no
	writable = no
```

---

