---
title: "limited or no connectivity"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by girard on 2007-08-01
i setup a peer to peer network with my fiesty desktop and xp notebook. it is working, but the problem is that it takes forever for things to get loaded. i searched the forum already, but it seems most problems are with slow networks (i'm taking this to mean, slow transfers such when copy pasting stuff from the shared folders, etc...). I don't have a problem with that i think because when they eventually get loaded, i can easily transfer files and folders from the shared folder both ways. what takes forever is the initial opening of the network folder. 

already tried lowering SO_SNDBUF and RCVBUF as mentioned in one of the threads, but it didn't help.

also, i'm not sure about the ipaddress of my linux. in ifconfig, which one is it? here mine:

> 
eth0      Link encap:Ethernet  HWaddr 00:E0:18:D9:4B:68  
          inet addr:192.168.252.249  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::2e0:18ff:fed9:4b68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:648160 (632.9 KiB)  TX bytes:151979 (148.4 KiB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1114 (1.0 KiB)  TX bytes:1114 (1.0 KiB)


this is my smb.conf

> 
[global]
    ; General server settings
    netbios name = kubli
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=4096 SO_SNDBUF=4096

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
    path = /home/kubli/shared
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = kubli
    force group = kubli
available = yes
browsable = yes
public = yes
writable = yes


i'm tracing this to the fact that in XP, it shows "Limited or no connectivity". this probably has everything to do, because the network is working, it's just slow which to me seems "limited"

i sure hope someone would be able to explain what's happening. thanks a lot!

---

