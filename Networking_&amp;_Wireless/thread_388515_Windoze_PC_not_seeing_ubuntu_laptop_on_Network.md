---
title: "Windoze PC not seeing ubuntu laptop on Network"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by The Judderman on 2007-03-19
Dear All,

I want to set up a Samba file sharing between my ubuntu laptop and my windoze PC, connected via a router. From my laptop, I can ping my PC on the network without any problems, but my PC doesn't see my laptop, so I am not able to set up Samba properly... Any ideas?

I have disabled my firewall, as my router acts as a router between my PC and the internet, and yet still no joy...

Would appreciate if you could give me some pointers...

Cheers,

The Judderman

---

### Post by Thirsteh on 2007-03-19
This might work:

On your Linux box, in a terminal, type: ifconfig

Locate and write down/remember the IP.

On your Windows box: Start->Run...-> \\192.168.0.1  

(insert IP :))

The automatic broadcasting/polling that Windows machines do, is, as far as I know, disabled in Samba by default. Might explain why your Linux box is not immediately visible.

---

### Post by dmizer on 2007-03-19
fantastic howto for setting up a samba server, first link in my sig.

this howto REQUIRES your windows machine to have a username and password login, so be prepared for that.  it's possible to configure your smb.conf file to allow unauthenticated connections, but i really would discourage this ... especially on a laptop.

---

### Post by The Judderman on 2007-03-20
Interestingly, it was your How to that I used to set up Samba, and it does seem to have worked beautifully... It is just that windows doesn't seem to find my laptop... I'll try what Thirstey suggested when I get home (at work at the mo!)

Thanks for a great and clear how-to dmizer!

The Judderman

---

### Post by dmizer on 2007-03-20
if you're still having problems, just post your smb.conf file here, as well as the output of:
```
smbtree
```
we'll see if we can't get it sorted for you.

---

### Post by The Judderman on 2007-03-23
smbtree doens't have any output. It just asks for my password, then nothing... My smb.conf file is as follows... Sorry I haven't answered quicker... Just a bit busy!!!

Thanks for taking a look at this!

[global]
    ; General server settings
    netbios name = LAPTOP
    server string =
    workgroup = JUDNET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = NO

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
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = peter
    force group = peter

---

### Post by The Judderman on 2007-03-23
Interestingly, when I put my IP address (for the laptop)in a browser on my windoze PC, it comes up with a samb0-images directory, so it must be picking up my laptop somewhere on the network, though it isn't able to ping it!!!

---

### Post by dmizer on 2007-03-24
sounds like a firewall problem to me.  if you've installed firestarter, you'll have to open up the samba port to your local network.  you may have to do something similar to your windows firewall as well.

---

### Post by The Judderman on 2007-07-12
I should have answered this ages ago to say that I did manage to sort it out... It was a firewall issue, and I had been using DansGuardian, but now I've just deactivated it all.. I've got a firewall in my router, which works beautifully, and now I can network seamlessly between my windoze machine and my Ubuntu! hopefully it will carry on working as nicely when I migrate to Feisty... I even managed to set up printers etc!!!

Thanks for all your help guys!

The Judderman

---

