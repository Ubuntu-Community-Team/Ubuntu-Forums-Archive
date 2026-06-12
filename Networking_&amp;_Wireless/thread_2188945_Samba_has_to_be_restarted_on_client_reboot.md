---
title: "Samba has to be restarted on client reboot"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by rathershocked on 2013-11-19
Hiya,

Using Ubuntu 12.10 (client) and 12.04 (server) and I have a somewhat annoying problem.  Every time I reboot my client computer I have to SSH back to my server and restart samba so that the client can mount the shared folders again.  Soon as I do a 'sudo smbd restart' and then a 'sudo mount -a' on the client, I'm back in business and I can see the mounted shares as normal.

smb.conf:

```
[global]    ; General server settings
    netbios name = BIGMOMMA
    server string =
    workgroup = WORKGROUP
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
    ;path = /var/lib/samba /profiles
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


[BigShare]
    path = /home/matt/Sharing
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = matt
    force group = matt

```

I have tried using the samba GUI application, but the same thing happens and so I'm using an older smb.conf that used to work well (in 10.04)..obviously it doesn't.  If I try to mount the samba share without restarting samba before hand I get:

```
mount error(6): No such device or address
```

Any help is appreciated.

---

### Post by Morbius1 on 2013-11-20
That's a rather odd symptom. Well, the symptom isn't odd it's the fix that's odd. One would think that restarting nmbd not smbd would fix it because of the rather primitive netbios mechanism that samba defaults to because it's set for a Windows network not a Linux/OSX network.

*** The "sudo mount -a" comment suggests that you have a entry in fstab to mount this share. Can you show us that line so we can see how it's set up.

*** Are you connecting to the server by ip address or by name? If it's by name see if after the next reboot you can access the server by it's mDNS qualified name instead:
```
nautilus smb://hostname.local
```
[COLOR=#0000cd][I]Where hostname is the host name of the server - and don't forget the ".local" part.

[/I][/COLOR][COLOR=#000000]There could be another explanation: It's not the restarting of smbd on the server it's the "sudo mount -a" on the client that's fixing things. It could be that fstab is executed before the network is up on the client.[/COLOR]

---

### Post by rathershocked on 2013-11-20
Thanks for the reply

I'm connecting by name, not IP - here's the relevant line in fstab:

```
//BIGMOMMA/BigShare    /media/bigmomma        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

if I try the mDNS qualified name, it comes up with a file manager window, with a directory to bigshare, but when I try to click into the shared directory, it tells me that it doesn't exist.

I've tried just mounting without restarting samba on the server and I just get the same error:

```
mount error(6): No such device or address
```

I was previously restarting both smbd and nmbd, but then, after fiddling, found that just restarting smbd on its own works.

Thanks for trying! =)

edit:

Just tried, restarting nmbd on its own (then remounting the client) doesn't work

---

### Post by Morbius1 on 2013-11-20
If you haven&#8217;t restarted smbd on the server yet does everything work if you pass the credentialed username to the server + mDNS:
```
nautilus smb://username@bigmomma.local
```

---

### Post by rathershocked on 2013-11-20
I get the same result, unfortunately - file manager will come up, try to log into the shared directory, password is requested but then says it doesn't exist.

Sorry for the silly questions, but do you think this may possibly be related to router issues - I know when I upgraded the server, my brother also was fiddling around with various bits and bobs in my router (old Linksys with Tomato) - haven't quizzed him about what he actually did as yet.

---

### Post by Morbius1 on 2013-11-20
It seems to me that if it was a router problem it would exist even after you restarted smbd on the server.

I wanted to pursue the mDNS route because I was convinced that this was a name resolution issue. The default netbios mechanism is one way and the mDNS way is another faster way but in this case both fail. 

It really does seem like smbd shuts itself off on the server and I can't imagine why it would do that on it's own and certainly not triggered by a samba client going away and coming back. There will always be a delay in the netbios name discovery mechanism when a new client enters the network - it could take several minutes. But hostname.local is immediate and doesn't have this delay issue. 

I'm really at a loss here trying to imagine a process that would result in this. Is this happening on all the clients to this server of just this one?

---

### Post by rathershocked on 2013-11-20
Hiya

I actually just reset tomato to defaults anyway..and as you suggest, no difference.

I was going to state that it happens on other client devices (I rarely use the share on other clients), but just checked and my netbook (Lubuntu 12.10) works absolutely fine - I don't have it perma-mounted in fstab, but going through network drives in nautilus, it displays the share with no issues.

Clearly this must be an issue with my main PC.  Thanks for trying to help..it's at least given me a pointer as to where the problem may lie =)

---

### Post by Morbius1 on 2013-11-20
I'm shutting down for the day but you might want to post the output of this command so folks here can see how your smb.conf is set up on the client that's having the problem:
```
testparm -s
```
Most of smb.conf deals with server configurations but there are items in there that affect the samba client even if you didn't install the samba server.

---

### Post by rathershocked on 2013-11-21
Thanks again!

```
Load smb config files from /etc/samba/smb.confrlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

---

### Post by bab1 on 2013-11-21
> **rathershocked said:**
> Thanks again!

```
Load smb config files from /etc/samba/smb.confrlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

No shares listed.  I guess you used the GUI to create the shares.

Either way let's see what shows with this command```
smbclient -L <SERVER_NAME>
```...where <SERVER_NAME> is the name of your Samba server.  You can use the IP address if you like.

[COLOR="#0000FF"]Edit:  I don't think the client is the problem.  In fact it looks like the client's smb.conf is original and unmolested.[/COLOR]

---

### Post by rathershocked on 2013-11-21
> **bab1 said:**
> No shares listed.  I guess you used the GUI to create the shares.

I didn't realise that you needed to list shares on the client smb.conf?  The server smb.conf is in the top post, if that is what you meant?

> Either way let's see what shows with this command```
smbclient -L <SERVER_NAME>
```...where <SERVER_NAME> is the name of your Samba server.  You can use the IP address if you like.

This gives me (with both name and IP):

```
session setup failed: NT_STATUS_LOGON_FAILURE
```

Thanks for the help

---

### Post by bab1 on 2013-11-21
> **rathershocked said:**
> I didn't realise that you needed to list shares on the client smb.conf?  The server smb.conf is in the top post, if that is what you meant?
> 
You DO NOT need to declare the shares on the client smb.conf.  That was my oversight.  




This gives me:

```
session setup failed: NT_STATUS_LOGON_FAILURE
```

Thanks for the help
It looks like the Samba server does not know who you are.  Do you have an Linux account on the Server?  Does that Linux account also have a Samba user account (smbpasswd -a)?

[COLOR="#0000FF"]**Edit: to show the accounts you use these commands**[/COLOR]```

getent passwd <username>

sudo pdbedit -L

```
 The first one is the Linux user.  The second one is the listing of all Samba users.

---

### Post by rathershocked on 2013-11-21
```
getent passwd matt

matt:x:1000:1000:[real name],,,:/home/matt:/bin/bash


sudo pdbedit -L

matt:1000:[real name]
```

Edit:  More info..

Checked on my netbook..the problem persists on there too (not sure why it worked before)..and is solved by the same process.

Putting guest to 'yes' in smb.conf does absolutely nothing, still can't display that share without restarting smbd.

---

### Post by Morbius1 on 2013-11-21
*** I was hoping for some kind of anomaly in the smb.conf on the client but it appears to be the standard default.

*** This is probably another rat hole since so far nothing explains why a restart of smbd on the server fixes everything but ....
Do you have any content in /etc/samba/smbusers on the server?

*** Restarting smbd wouldn't be the correct fix for this either but is there a duplication of ip addresses in this network?

[COLOR=#0000cd] **EDIT**: Didn't see your edit:[/COLOR]
>  Putting guest to 'yes' in smb.conf does absolutely nothing, still can't display that share without restarting smbd.                 
Well, in all likelihood you needed to restart smbd for the change to guest access to take affect so I'm not sure if that tells us anything - *unless you also rebooted the client*.

---

### Post by rathershocked on 2013-11-21
> **Morbius1 said:**
> *** I was hoping for some kind of anomaly in the smb.conf on the client but it appears to be the standard default.

*** This is probably another rat hole since so far nothing explains why a restart of smbd on the server fixes everything but ....
Do you have any content in /etc/samba/smbusers on the server?

*** Restarting smbd wouldn't be the correct fix for this either but is there a duplication of ip addresses in this network?

[COLOR=#0000cd] **EDIT**: Didn't see your edit:[/COLOR]

Well, in all likelihood you needed to restart smbd for the change to guest access to take affect so I'm not sure if that tells us anything - *unless you also rebooted the client*.

Hello!

In the smbusers, it just says "matt=matt" when opened with nano, though given that it does the same thing when trying to access as guest, I'm not sure if that's where the problem lies...and yep, I rebooted the server then rebooted the client - every time I try something I do the same.

I'm not sure how to test for duplication of IP addresses, sorry =/

I'll try purging everything samba flavoured from my server and reinstalling, but I've kinda already tried that, so I'm not hopeful

Anyway, I really appreciate the help from both of you, but I suspect I'm going to actually get off my lazy **** and learn more about how networking and samba work.

---

### Post by bab1 on 2013-11-21
> **rathershocked said:**
> Hello!

In the smbusers, it just says "matt=matt" when opened with nano, though given that it does the same thing when trying to access as guest, I'm not sure if that's where the problem lies...and yep, I rebooted the server then rebooted the client - every time I try something I do the same.

I'm not sure how to test for duplication of IP addresses, sorry =/

I'll try purging everything samba flavoured from my server and reinstalling, but I've kinda already tried that, so I'm not hopeful

Anyway, I really appreciate the help from both of you, but I suspect I'm going to actually get off my lazy **** and learn more about how networking and samba work.

If you purge everything and start over, just install samba (not Samba4).  No helper applications.  The configuration is trivial once you understand how it works.  Both @ Morbius1 and I understand and can help you.  There are only 3 things to setup in a typical small LAN.  These are the *_netbios name =_* and *_name resolve order = _* directives and the actual shares.  The first 2 take care of the networking.

What have you actually used to configure Samba?  What have you modified other than the smb.conf file?

---

### Post by Morbius1 on 2013-11-22
>  I'm not sure how to test for duplication of IP addresses, sorry =/
Just run one of the following commands on each Linux box:
```
nm-tool
ifconfig
```
The only time this is usually an issue is if you set a static ip address on a box and it fell within the range of ip addresses that the router is giving out via DHCP. Under those conditions it's possible that there could be 2 machines with the same ip address depending on the sequence of which machine was booted. If this was the problem restarting smbd would do nothing but I'm just trying to eliminate the usual suspects.

*** If you are or already have reinstalled samba make sure you include samba-common since that's where smb.conf comes from.

*** If you are starting from the beginning you could do the "netbios name" and "name resolve order" thing by adding to the [global] section of smb.conf the following lines - I would put them right under the workgroup line:
```
netbios name = bigmomma
name resolve order = bcast host lmhosts wins
```
I wouldn't get too hung up on the netbios thing at the beginning - in an all Linux or Linux / OSX network you can make it work with the whole netbios / name resolve process disabled if you wanted. I would do all experiments using the ip address of the server so as to eliminate any peripheral issues:
```
nautilus smb://192.168.0.100
```

---

