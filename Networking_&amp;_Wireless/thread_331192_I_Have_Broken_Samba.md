---
title: "I Have Broken Samba"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by l951b951 on 2007-01-04
I had samba sharing working as soon as I installed it.  I used Places=>Connect to server and connected to my windows share workgroup "linksys".  It worked until I shut my computer down.  Now I can't even browse windows networks to see the network.  My other linux machine can see and access the network.  
My router is set for dynamic IP addresses, not static.  I'm thinking this might be the problem.
I have used 3 different Samba howtos and have changed my smb.conf file with each one trying to get it to work.  
I am using a linksys WRT54G router.  I am connected to it wirelessly.
I have gone into windows connections before and the workgroup "linksys" has a link mounted on my desktop.  
I have 2 windowsXP computers running and 2 linux machines running.  Both Linux machines have different host names, but I log into both as "levi".  Could that cause some conflict?
Here is my smb.conf as it now stands.


> [global]
    ; General server settings
    netbios name = LINUX-LAPTOP
    server string =linux-laptop
    workgroup = LINKSYS
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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
    path = /levishare
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = levi
    force group = users
available = yes
public = yes
writable = no

---

### Post by Spano on 2007-01-04
To my knowledge dynamic IP shouldn't be a problem, however I set my machines static so they're easier to keep track of when configuring new software.  I'd suggest simplifying  your smb.conf to get things working.  All I bother with is setting security to 'user' and defining 'homes'.  I attached a copy of mine.  Add more options one at a time after your connected.
Remember Samba can take a few minutes to identify other machines after a reboot.  Also check your firewall.

---

### Post by l951b951 on 2007-01-07
I am still having Samba woes.  I tried using swat to configure my smb.conf file.  Nothing happened.
I actually copied the smb.conf from my Fedora Core 6 machine (which works) and copied it to my Ubuntu /etc/samba/smb.conf.  My samba is still not working on this machine.  When I browse for networks I see the option for "Windows Networks", but when I open that folder it immediately shows nothing.  Reloading the folder does nothing to help.

So at this point I'm stuck.  I've tried reading every wiki and how-to there is.  
Since I have used swat and also copied a known good smb.conf file, I'm thinking my problem is with something outside of samba.  I am thinking that my smb.conf file should have had a working configuration somewhere through this troubleshooting process.  

So my question is, what do I need to do check for next?  To my knowledge, I am not running a firewall (I haven't installed one).  If I ping a winxp computer by IP Address, I can get a response.  But I still can't see the windows network, and I use dynamic IPs with my linksys router.  

Can someone give me something to try next?

---

### Post by l951b951 on 2007-01-07
It turns out I wasn't asking the right question.  Samba wasn't my problem.  I couldn't access my WinXP shares on the network.  Through something I did, I had changed my domain name, and just wasn't part of the XP network.  
As I was reading, I finally realized that Samba just lets other computer browse my computer.  My problem was trying to browse the other computers.  
Checking my Domain should have been first on my list, but I changed it finally and it works.
Additionally, my computer name had been linux-laptop and I changed it to tuxtop.  Not sure if the hyphen matters, but I changed it just in case.  




> **l951b951 said:**
> I am still having Samba woes.  I tried using swat to configure my smb.conf file.  Nothing happened.
I actually copied the smb.conf from my Fedora Core 6 machine (which works) and copied it to my Ubuntu /etc/samba/smb.conf.  My samba is still not working on this machine.  When I browse for networks I see the option for "Windows Networks", but when I open that folder it immediately shows nothing.  Reloading the folder does nothing to help.

So at this point I'm stuck.  I've tried reading every wiki and how-to there is.  
Since I have used swat and also copied a known good smb.conf file, I'm thinking my problem is with something outside of samba.  I am thinking that my smb.conf file should have had a working configuration somewhere through this troubleshooting process.  

So my question is, what do I need to do check for next?  To my knowledge, I am not running a firewall (I haven't installed one).  If I ping a winxp computer by IP Address, I can get a response.  But I still can't see the windows network, and I use dynamic IPs with my linksys router.  

Can someone give me something to try next?

---

