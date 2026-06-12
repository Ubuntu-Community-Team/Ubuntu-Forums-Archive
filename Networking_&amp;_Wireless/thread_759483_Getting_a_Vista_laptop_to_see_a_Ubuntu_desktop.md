---
title: "Getting a Vista laptop to see a Ubuntu desktop"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by SteveHall on 2008-04-19
I'm fairly new to Ubuntu, but am pretty happy with most of the stuff I've been able to do.  I've recently got a laptop with Vista loaded on it and I'm trying to get them to see each other so I can share photographs and music files.  I've tried following some help guidelines and I've looked through a number of similar posts, but I've not been able to get them to see each other.  I'd appreciate some help trying to get this set up.

Both machines are connected to a Router modem.  They can both get onto the internet and both machines can ping each other, so I don't think it is a connectivity problem.

Attached below is my smb.conf file that got set up when I was following some help guidelines.  I have the workgroups set up the same on both machines.


_smb.conf file_

[global]
    ; General server settings
    netbios name = Study-Linux-Desktop
    
    workgroup = HALL
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
    force user = steve
    force group = steve
available = yes
browsable = yes
public = yes
writable = no

---

### Post by jonandrews on 2008-04-19
I've put together a guide to networking Ubuntu & Windows PC's on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

It was written around Windows XP, but a number of forum users have told me that it worked fine for them using Vista, so hopefully it can help you.

---

### Post by SteveHall on 2008-04-20
Thanks for pointing me in the direction of this guide.  It looks really clear and easy to follow.

Unfortunately I'm stuck on Step 1.  I'm not really sure whether it's a problem with Ubuntu settings or my Vista settings.  When I go into [COLOR="RoyalBlue"]Places > Network[/COLOR] I can see the Windows Network icon.  When I double click on this icon I can see the name of my Windows Network, in my case [COLOR="RoyalBlue"]HALL[/COLOR].  However when I double click on [COLOR="RoyalBlue"]HALL[/COLOR] I get an error message [COLOR="Red"]The folder contents could not be displayed.  Sorry, couldn't display all the contents of "Windows Network: hall"[/COLOR].  I've checked back in my Vista laptop.  I have in the [COLOR="RoyalBlue"]Network and Sharing Centre[/COLOR] settings set up so it is a [COLOR="RoyalBlue"]Private Network[/COLOR] (i.e. easy to see other computers and be seen by others on the network).  I have [COLOR="RoyalBlue"]Network discovery[/COLOR] set to [COLOR="RoyalBlue"]On[/COLOR], [COLOR="RoyalBlue"]File Sharing[/COLOR] set to [COLOR="RoyalBlue"]On[/COLOR], [COLOR="RoyalBlue"]Public Folder sharing[/COLOR] set to [COLOR="RoyalBlue"]On[/COLOR].  I have set up a folder to be shared and set it up so that [COLOR="RoyalBlue"]Everyone[/COLOR] can share it and that no specific user name and password is required to share it.

Do you have any ideas on where I should be investigating further?  I'd appreciate any steer you could provide.

---

