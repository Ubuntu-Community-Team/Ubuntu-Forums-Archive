---
title: "domain accounts"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by salvor_hardin on 2007-12-05
I have troubles adding acounts to unix so I can access from it from xp. I added machine and user but still when i try to connect it says "cannot log in from this workststion". im trying to connect from xp to domain which is set up through samba. here is my smb.conf file:

```
[global]
    ; General server settings
    netbios name = SALVOR
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = domain
    preferred master = yes
    domain master = yes
    local master = yes
    domain logons = yes
    
    null passwords = true
    encrypt passwords = no
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

    ; domain administrators
    domain admin group = administrator	
    domain admin users = root


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

;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/hda1/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = salvor
    force group = salvor


;[juresdir]
    [Jure]
    comment = Jurin folder
    path = /home/jure
    valid users = jure
    public = no
    writable = yes
    printable = no
    guest ok = no
    force user = jure

;[rogersdir]
    [Roger]
    comment = Rogerov folder
    path = /home/roger
    valid users = roger
    public = no
    writable = yes
    printable = no
    guest ok = no
    force user = roger


```

xp is xp pro! don't know how to add machine account to domain so i can access it from xp. help me please

---

### Post by gazj on 2007-12-05
you pretty much have to create a unix account for every machine, see link below as an example, i have not done this for a long time, but i don't think it has been changed.

[http://www.yellowbugcomputers.com/techdocs/sambadomain.html](http://www.yellowbugcomputers.com/techdocs/sambadomain.html)

also change security from domain to user, when set to domain, the samba server will go looking to verify users against a windows dc on the domain

---

### Post by salvor_hardin on 2007-12-05
thx, this is simpliest so far. i checked my smbpasswd file and there is nothing inside. thats where problem probably was.

---

### Post by gazj on 2007-12-05
your welcome :)

---

### Post by salvor_hardin on 2007-12-07
Ok, i did everything like there and on bunch of other sites. Refuses to connect me from xp. In first it said that no account and now it says that domain couldnt be contacted or it isnt there. And one more thing, it doesnt want to make an entry for machine user in smbpasswd file. And I forgot my password in for root that i added for adding domain members. In simole, it wont work.

---

### Post by salvor_hardin on 2007-12-07
And here is output of my smbclient localhost: 

> Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        print$          Disk
        MyFiles         Disk
        Jure            Disk      Jurin folder
        Roger           Disk      Rogerov folder
        IPC$            IPC       IPC Service (server_lan)
        ADMIN$          IPC       IPC Service (server_lan)
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        SALVOR               server_lan

        Workgroup            Master
        ---------            -------
        MSHOME               SALVOR
        WORKGROUP            FRANO


and output from the same just not xp but win2000!

> Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        print$          Disk
        MyFiles         Disk
        Jure            Disk      Jurin folder
        Roger           Disk      Rogerov folder
        IPC$            IPC       IPC Service (server_lan)
        ADMIN$          IPC       IPC Service (server_lan)
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        SALVOR               server_lan
        VIRTUALNI1

        Workgroup            Master
        ---------            -------
        MSHOME               SALVOR


---

### Post by gazj on 2007-12-07
Hi sorry to see your still having trouble

are you trying to just access the shares in a workgroup, or are you trying to join your machines to a domain, or have you succesfully joined a domain and trying to access shares.

---

### Post by salvor_hardin on 2007-12-07
i'm trying to join xp to ubuntu domain. i have troubles adding users to smbpasswd file. in most cases when i try to join domain it says "invalid username or pass" and sometimes it says "cannot locate domain":confused:
I can't join xp to ubuntu/samba domain!

---

