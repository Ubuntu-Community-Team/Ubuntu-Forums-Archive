---
title: "Can not access XP shares from nautilus"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by ceckard on 2008-07-14
I am having problems access my XP shares using samba. When I go to places and select network I can see all of the machines on my network but clicking any of them just brings me to a blank screen without any of my shared folders/files showing. If I type the IP of the XP machine (192.168.1.101) I can see the shared folders. 

I can ping all machines
smbtree shows all machines and shares within them.
I can access the ubuntu shares from the XP machines.

Here is the output of "**sudo iptables -nvL -t filter**":
Chain INPUT (policy ACCEPT 12088 packets, 8868K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 10107 packets, 1664K bytes)
 pkts bytes target     prot opt in     out     source               destination 

Here is the output of "**ps -aux | grep winbind**"
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
chad     18688  0.0  0.0   3004   764 pts/0    R+   15:50   0:00 grep winbind

Here is a copy of my **smbf.conf** file:
[global]
    ; General server settings
    netbios name = LENOVO
    server string =
    workgroup = WORKGROUP
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
    force user = chad
    force group = chad

I have read through the following fourms:
[http://ubuntuforums.org/showthread.php?t=820327](http://ubuntuforums.org/showthread.php?t=820327)
[http://ubuntuforums.org/showthread.php?p=5155923#post5155923](http://ubuntuforums.org/showthread.php?p=5155923#post5155923)
Stormbringer's Guide:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ceckard on 2008-07-15
Surely I can't be the only one having this problem. I've read of other people with the same problem. Hopefully someone has a solution/work around for this.

Another issue that I forgot to mention. I have a NAS box. I can see it listed, but I can not access by the netbios name or the IP address. Any ideas on this?

Any help with this would be greatly appreciated.

---

### Post by motin on 2008-08-20
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/236903)

Use smb4k or konqueror as a work around...

---

