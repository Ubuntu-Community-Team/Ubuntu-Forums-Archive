---
title: "hard time setting up SAMBA"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Buz_Light on 2008-07-18
Some help here would be appreciated. I've been trying to setup my network for a while and just can't do it. 
Although I've been using Ubuntu for a while, I still consider myself a beginner.

----------------
First, let me explain how is my network connected and why I want to use SAMBA...

My desktop computer (running dual boot Hardy-64 / Vista home premium) connects to my first router (gateway 192.168.1.1) with a static IP.
A second router also connect to my first router via a static IP (add to use two router because the wireless signal was really bad from down- to upstair). 
This second router (gateway 192.168.0.1) assign a static IP to my Xbox media center and an adress to my laptop (via DHCP). My laptop is also on dual boot (XP / Hardy).

My needs are to access my Backup hard drive and my media hard drive on my desktop computer from both my Xbox and my laptop (from both XP and Hardy).
-----------------

Here is my smb.conf file : 
obtained following this guide : [http://ubuntuforums.org/showpost.php?p=1174825&postcount=1](http://ubuntuforums.org/showpost.php?p=1174825&postcount=1)

```
[global]
    ; General server settings
    netbios name = Desktop
    server string =
    workgroup = infinity
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
[DVD-ROM Drive]
    path = /media/cdrom0
    browseable = yes
    read only = yes
    guest ok = yes

[Backup]
    path = /media/Backup/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = carl
    force group = carl

[PCdisk]
    path = /media/disk/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = carl
    force group = carl
```

If I run 
```
smbclient -L Desktop
```
from my Desktop computer, I receive 
```
Domain=[DESKTOP] OS=[Unix] Server=[Samba 3.0.28a]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk     
    DVD-ROM Drive   Disk     
    Backup          Disk     
    PCdisk          Disk     
    IPC$            IPC       IPC Service ()
    scx4100         Printer   printer on Carl-PC
    PDF             Printer   PDF
    backup1         Disk     
    xbox            Disk     
Domain=[DESKTOP] OS=[Unix] Server=[Samba 3.0.28a]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
    INFINITY 
```
which let me think my "Backup" and "PCdisk" share are set correctly.

Now, if I try to access these share from my laptop (client side) under hardy, using
```
smbclient  //Desktop/Backup
```
i get the following error 
```
timeout connecting to 208.67.217.132:445
Error connecting to 208.67.217.132 (No route to host)
Connection to Desktop failed (Error NT_STATUS_HOST_UNREACHABLE)
```

There it is, can you help me resolve this problem?

---

### Post by Buz_Light on 2008-07-18
a little more

if I try with my local IP
```
smbclient //192.168.1.100/Backup
```
I receive the following:

Password: 
Domain=[DESKTOP] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_NO_SUCH_GROUP

Hope it helps...

---

### Post by Buz_Light on 2008-07-21
up

---

### Post by s6long1 on 2009-02-03
bump!

I am having the same problem. 

```
sudo mount.cifs //192.168.1.117/share /media/lan -o username=steve,password=******

```

gives me "mount error 13 - No route to host"


```
smbclient -L BRITTANY-PC
```

gives me:
"Error connecting to 192.168.1.117 (No route to host)
Connection to BRITTANY-PC failed (Error NT_STATUS_HOST_UNREACHABLE)"

I am connecting through a wireless router, and I disabled the firewall on the Vista machine I'm trying to connect to. What should I try next?

---

### Post by Coreigh on 2009-02-03
can you "see" the server?
```
sudo ping -c 4 192.168.1.117
```

Username and password are the username and password for the server account?

On XP and 2003 there is extra security on shares. Have you gone to the sharing tab and explicitly granted FULL permission to 'steve' or everyone?

Can you see the server from the "Connect To Server" in the "Places" menu?

---

### Post by grungedoobie on 2009-02-28
Trying to set up Samba.  Have pulled out all head and facial hair.  Am currently working on body hair!!  :(

Have tried more than a dozen tutorial and help based samba configurations including a plethera of combinations in between.  As well as a couple more derived from linux scholastic books that are available to me (man, those books are mega huge).

Here is the home network setup.  Four computers connected to a router/firewall.  One is to be used as a full access file share service to the other three (one of which is using windows, the rest are linux boxes).  I would like to set up user specific HDD locations on the server in the future, but for right now, I would just like to see the thing work.

From the get go I was able to get the server to transmit itself on the LAN which is visible to all other computers.  However, when I try to access the shares via Konqueror, Dolphin or Shell I get this message: "timeout on server".

Here is the current smb.conf file :

## Samba Example  by: Me

# Global Settings

[global]
        workgroup = HOGTIED
        server string = %h server (Samba, Ubuntu)
        dns proxy = yes

#  Debugging/Accounting/Logging

        log file = /home/billybob/samba/logs/log.%m
        max log size = 1000
        syslog = 0
        panic action = /home/billybob/samba/panic-action %d

#  Authentication

        encrypt passwords = true
        passdb backend = tdbsam
        obey pam restrictions = yes
        invalid users = 
        unix password sync = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* $
        pam password change = yes
        map to guest = bad user


# File Shares

[shares]
        path = /home/billybob/shares
        browseable = yes
        writable = yes
        guest ok = yes
        read only = no
        admin users = billybob
        invalid users =
        guest account = billybob@junker
        force user = billybob@junker
        create mask = 0777
        directory mask = 0777
        force create mode = 0777
        force security mode = 0777
        force directory security mode = 0777
        force directory mode = 0777
        locking = no


Here is the ouput of the testparm command:

billybob@junker:/$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[shares]"
Global parameter guest account found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = HOGTIED
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /home/billybob/samba/logs/log.%m
        max log size = 1000
        panic action = /home/billybob/samba/panic-action %d

[shares]
        path = /home/billybob/shares
        admin users = billybob
        force user = billybob
        force group = billybob
        read only = No
        create mask = 0777
        force create mode = 0777
        force security mode = 0777
        directory mask = 0777
        force directory mode = 0777
        force directory security mode = 0777
        guest ok = Yes
        locking = No
billybob@junker:/$       


oh, and here is the listing that I get when I check the addy assigned for the server.

anotherbox@nottheserver-desktop:/$ sudo smbclient -L <server addy> -U%
[sudo] password for anotherbox:
Domain=[HOGTIED] OS=[Unix] Server=[Samba 3.2.3]

        Sharename       Type      Comment
        ---------       ----      -------
        shares          Disk
        IPC$            IPC       IPC Service (junker server (Samba, Ubuntu))
Domain=[HOGTIED] OS=[Unix] Server=[Samba 3.2.3]

        Server               Comment
        ---------            -------
        JUNKER                junker server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        HOGTIED
anotherbox@nottheserver-desktop:/$


and here is the output for a ping from another box to the server

anotherbox@nottheserver-desktop:/$ sudo ping -c 4 <server addy>
[sudo] password for anotherbox:
PING <server addy> (<server addy>) 56(84) bytes of data.
64 bytes from <server addy>: icmp_seq=1 ttl=64 time=0.521 ms
64 bytes from <server addy>: icmp_seq=2 ttl=64 time=0.258 ms
64 bytes from <server addy>: icmp_seq=3 ttl=64 time=0.518 ms
64 bytes from <server addy>: icmp_seq=4 ttl=64 time=0.261 ms

--- <server addy> ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.258/0.389/0.521/0.131 ms
anotherbox@nottheserver-desktop:/$



If there is anyone who can help, please post.  I'm running out of hair to pull.

I can post the samba log files if asked, but it may take a while to edit the nomenclature.

Luck to all, the grunge

---

### Post by grungedoobie on 2009-03-01
All of that goobudy-goo and guess what.  I am still unable to use samba shares with konqueror, dolphin or from command prompt.

I was hunting down a port sniffing program I had just installed and came across "Smb4K" which I had downloaded a while back not knowing what it was.

Smb4K is able to connect to the samba shares on the server computer.

Interesting, even though it makes very little sense to me.


Bewildered,  the Grunge.

---

### Post by grungedoobie on 2009-03-09
Does anybody know of a website that has posted most or all of samba's "smb.conf" file commands in a clear and logical order with some description of what the commands do?

Perhaps I'm just missing something that doesn't show up readily on the "dummy can do it" config setups and helps.

The Grunge.

Thanks in advance for any advice.  :D

---

### Post by grungedoobie on 2009-03-22
I've found my problems.  

#1:  Samba is huge and I don't know enough to set it up properly.  

#2:  There are other packages running along side of Samba that I didn't know were there, so I'll either have to learn how to configure/remove/sidestep them as well.

This may take me a while, but I'll post when I am able to get Samba running.

The Grunge.  ;)

---

### Post by lswartz on 2009-03-23
Congrats Grunge. Isn't it great when you find a solution. I'm on day 6 with my Ubuntu Dell Mini9, got my wireless to work at home on day 4 & connected to my shared printer on day 5. Well, my son got the printer to connect.

I am really impressed with Ubuntu. It seems to do everything that Win XP Pro does but I have to learn where to look. 

Sounds like the OP should be talking to you about his problem.

---

### Post by grungedoobie on 2009-04-14
I've finally got Samba running.  It's not perfect, but that's probably just 'cause there are too many ways that too many OS's prefer to connect to a shares computer.

I've had to start from the ground up beginning with the share server.  It's pretty complicated, and I'll put together a chronological order as to how I was able to do it.

I'll lay it all out before posting so that I don't forget any steps.  All it takes is one mis-step and it will bring you to tears.

My setup is based on the assumption that the shares server is just that and nothing else.  Additional software installs on the server comp may throw a mud brick in the wrong place causing additional tears.

Anyhow, I'll put together a "How - To" and post back here.

The Grunge

---

### Post by eudemus on 2009-05-06
Please do!

---

### Post by MysticGold04 on 2009-05-06
Yes, I will agree... Samba is somewhat of a bear to get running correctly.  My issues were I didn't have my other PC's in the hosts file, so that when I tried to ping them, it went out to the internet to reach other machines.  Also, I forgot to create my "mapped users" file that was specified in my smb.conf file... I ended up configuring my printer to be shared via IPP with cups and stopped the samba services for now.  Once I study up on it a little bit more, I'll feel more confident.  The only reason I was running samba was to share my printer to Windows clients.

---

### Post by capscrew on 2009-05-06
> **MysticGold04 said:**
> ... I ended up configuring my printer to be shared via IPP with cups and stopped the samba services for now.  Once I study up on it a little bit more, I'll feel more confident.  The only reason I was running samba was to share my printer to Windows clients.

Samba is a lot of overhead just to share a printer.  CUPS/IPP is perfectly fine if you are not sharing files.

---

### Post by grungedoobie on 2009-05-12
Well, here it is, and it's only taken me five hours to condense the soup of 4 months work and hair loss.

It is working for me, and I hope this works for you too.


As far as printers go, I may have had my fill of Samba for a bit.  I think I'll play with DNS'ing for a bit and see how that fares.  I hear that having a local caching Domain Name Server can cut time from web surfing.  Perhaps it's worth a go.  Ought to be interesting whatever the outcome.

Best of luck to all of you who play with Samba.

The Grunge.  :guitar:

P.S.  Let me know if the .txt doesn't show or work with your text editor, and I'll post it again.

Thanks mostly to my older brother for believing in me when I didn't believe in myself.  Thanks also belongs to the multitude of websites and forums I've scoured for the info used in the samba.conf file.  (too many for me to remember them all, lol :p )

---

### Post by grungedoobie on 2009-05-12
GGRRRRRR!!!!!!!!!!!!!!!!!!

I found a weak point in the text file!!

Here's the explanation.

I hope this doesn't mess anybody up!

In the smb.conf file of Part 7, it reads like this:

     ; This section opens up a free for all shares section that even Windows can recognize.
[Shares]
    path = <enter directory location with which to place shared files I.E. /whatever/mountpoint/public/share>
    browseable = yes
    read only = no
    writeable = yes
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = <enter name of user to force>
    force group = <enter name of 'user' to force>

     ; End of section "Shares"


Where you see the parts that say <enter name of user to force> that user and group entry ties in with the following part.  They need to be the same user and group for the thing to work right:

# Part 9

#  We're headed down the home stretch now.  The following commands will tie in the free for all shares between Samba and the System.
#  Note:  Some systems have to have a password shares with read/write access even if their public shares and free for all is being forced by the config file.  The following will give all local machines access to the shared directory whether their terminal requires usernames and passwords or not.


sudo adduser --home <directory of public share I.E. /whatever/mountpoint/public/share> <share>


#  Note:  When the steps take you to groupname and password, just use <share> to keep things simple.


sudo smbpasswd -a <share>



Where <share> is put in needs to be the same as the smb.conf file share section.

Hope this clears that up.  Luck :)


The Grunge

---

