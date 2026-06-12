---
title: "Yet Another Samba Issue"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by shawn_duggan on 2006-11-24
I have followed several how-to's and guides I have found, but I still cannot get either my Ubuntu wireless laptop or desktop XP SP2 machine to see each other on my network (DHCP).

My Windows and SMB user I tried to set up are both "Shawn".   I did give the Samba user the same password as the Windows user.  Below is smb.conf.  I'm feeling a bit stumped.  Other than this I have everything working on my laptop (even the wireless).  Thanks to any who choose to help.  ](*,) 

```

[global]
    ; General server settings
    netbios name = ThinkPad
    server string =
    workgroup = TERRANOVA
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

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

[SharedDocs]
    path = /home/shawn/SharedDocs
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = shawn
    force group = shawn

```

---

### Post by trubblemaker on 2006-11-24
windows fire wall off? sharing turned on?
can you ping the computer?

what are the result of sambatree, (can't remember think it asks for root password)


some places to start, 

man smbclient for ways to use the commmandline to check things out, a lot easier to troubleshoot that way than with a gui.

---

### Post by shawn_duggan on 2006-11-24
Thanks for your reply.

FireStarter running on Ubuntu laptop.  ZoneAlarm running on XP desktop.  My 2 windows machines (wired) on this network can see each other and share files ok.

smbtree returns nothing.  No errors, just the command line back.  testparm shows no errors.

---

### Post by trubblemaker on 2006-11-24
in zone-alarm click on > firewall what ip's are in your trusted zone?  Make sure that Ubuntu box is in that range.  

can you ping the xp boxes, is there anyother way to test the lan connectivity,

 or are they all on a router and you know they can talk.

smbtree no output = it found nothing 

I vote connectivity issues, 'caused by firewalls.

I think that you can test in a browser with
```
smb://192.168.1.100
```
where the above is one of your machines ip's but don't quote me as I'm on a windows box and can't test it.  I think You do need smbfs  to use this test but I'm not sure

---

### Post by shawn_duggan on 2006-11-24
I never thought to try entering an IP for my XP box in Nautilus. I had been trying to locate each machine by hostname.  When I do this I can access and write to the XP shared folders.  My XP machine however still cannot see my ubuntu laptop at all.  But I can work around that.  If you have any idea on how to fix that it would be great.

Thank you - I do appreciate your help.

---

### Post by trubblemaker on 2006-11-24
hey you find the solution tell me, I had it running perfect, it was some simple setting, but then i upgraded at it broke, 'cause I know the work around I haven't ever fixed it.  if you come up with a fix let me know

---

### Post by l|s on 2006-11-24
I don't know whether this will help or not but there was another user with a similar problem as yourself.

It turns out that firestarter was blocking broadcast traffic.

[http://www.ubuntuforums.org/showpost.php?p=1769994&postcount=14]("http://www.ubuntuforums.org/showpost.php?p=1769994&postcount=14")

---

### Post by trubblemaker on 2006-11-25
doesnt' help me but I hope it helps others thanks for posting

---

