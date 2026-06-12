---
title: "Samba and Windows"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by poordamnedfool on 2008-02-28
I have samba configured and installed onto my server, when ever i try to connect via a windows machine by mapping the drive, the login window pops up i type the user name and password in and it gives me an error message.  the second problem i have is that mac books cant access the server, will that be fixed when samba is working correctly?

---

### Post by NullHead on 2008-02-29
you can try this```
sudo smbpasswd -a <username>
``````
sudo smbpasswd -e <username>
``````
sudo /etc/init.d/samba restart
```

and the user name and pass you put in will be what you use for windows's login prompt.

---

### Post by poordamnedfool on 2008-02-29
I did that, this is why is confusing me so much... i set up two different login names and passwords and neither of them would give me access to the server

---

### Post by jhetrick62 on 2008-02-29
How is your samba config file set up?  If it is security=user and it is using PAM, then you have to have a vailid user account on Ubuntu even though you will use your samba passwd with it.

Post your /etc/samba/smb.conf file.  Macbook will work also when samba works.

Jeff

---

### Post by superprash2003 on 2008-02-29
check to see if your steps in setting up samba is similar to the one in [http://ubuntuguide.org](http://ubuntuguide.org) they have a very easy to follow samba tutorial!!

---

### Post by poordamnedfool on 2008-02-29
here is a copy of the smb.conf... i followed the tutorial and still have problems...

thanks for all the help

```
[global]
    ; General server settings
    netbios name = GOATSERVER
    
    workgroup = mshome
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
    path = /home    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = jqaskwig
    force group = jqaskwig
available = no
browsable = yes
public = no
writable = no

[samba]
path = /home/samba
available = yes
browsable = yes
public = yes
writable = no
```

---

### Post by Eiríkr on 2008-03-01
> **poordamnedfool said:**
> I did that, this is why is confusing me so much... i set up two different login names and passwords and neither of them would give me access to the server

Ideally your Windows and Linux usernames and passwords **should be identical**.  See if you can set up a username and password on the Linux machine that matches your Windows username and password.  Remember that the Linux username must actually exist as a system username; it's not enough to just enter the username into smbpasswd.  

There are ways around this problem if for any reason you cannot have matching Win-Lin usernames and passwords, but they add additional layers of complexity.  Remember the KISS principle -- keep it simple.  :)

Cheers,

Eiríkr

PS -- Also, what, exactly, is the error message you get when attempting to map a drive from Windows to the Linux share?

---

### Post by poordamnedfool on 2008-03-01
ok. ill try to match the user name and password of the windows machines tonight when i get home from work and i will find out what that error message is saying at that time too... thanks  ohh the mac book still cant see the server, i have both NFS ans SMB set up on it...

---

### Post by Eiríkr on 2008-03-01
The thing about NFS is that it is simple.  It's so simple, in fact, that it doesn't include any of the braodcasting capabilities of SMB.  That's both a blessing (in security terms), and a bother (in convenience terms).  Ubuntu comes with (or at least you can easily get via synaptic) a package called **avahi**, which is the Linux implementation of the **zeroconf** spec that Apple's been pushing for zero-configuration networking -- a fancy way of saying that computers will be able to recognize each other and their services without the user needing to muck about.  It's not truly "zero" config yet, but it's definitely getting easier.  I wrote an extensive post about setting up avahi to advertise NFS shares for my own iBook.  Have a look [post=4387032]here[/post] and see if you can use avahi for your own NFS shares.  It's a bit complicated, but just follow the directions and it'll work.  I'm also happy to answer any questions.  :)

Cheers,

Eiríkr

---

