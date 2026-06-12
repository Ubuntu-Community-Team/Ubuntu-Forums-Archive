---
title: "Transfering files from Xubuntu to XP"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by jrjvai on 2007-09-22
Hi!

What I would like to do is transfer several GB of files from my Xubuntu 7 desktop to a Windows laptop. I am aware that there a countless guides on how to do this and I have tried about ten of these and all have failed and some have resulted in catasrophies. So I'll start a new thread.

I think  I have three possible ways of doing this: directly connecting the computers with a LAN cable (is RJ-45 up to the task?)+samba, using my ADSL modem/switch, and using a Seagate FreeAgent drive. Whatever is the easiest way suits me. 

When I despaired after failing all these I even tried using a memory stick. Needless to say I failed that too. Couldn't find out how to make multiple volume archives in Linux. This can't be  too hard but I really wouldn't like to have to resort to this as it's a small memory stick.

If some extra information is required please ask away.

Any help would be appreciated!

---

### Post by ifconfig on 2007-09-22
Hi.

Aren't both computers connected to your switch today?

Samba is nice and working well and there's a good guide to Samba here.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Why I would prefer Samba is that you will be able to transfer files from the Xp to Xubuntu and Xubuntu to Xp. Because you have can create shares and mount shares in both systems. Which is good for future file transfers.

Another way is installing a ftp server to one of the computers and connect with the other to make the transfer. But, if you want to connect both computers from the other you will need to install a ftp server on both machines. This is why I would prefer using Samba.
A guide for install ftp. [http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)

Good luck!

// Magnus

EDIT: Forgot url about ftp install

---

### Post by jrjvai on 2007-09-22
If I use samba should the computers be directly connected or through the switch?  Previously I have tried samba and a direct connection.

---

### Post by ifconfig on 2007-09-22
> **jrjvai said:**
> If I use samba should the computers be directly connected or through the switch?  Previously I have tried samba and a direct connection.

It doesn't matter. I can't see any reason connecting the computers directly except if both computers have gigabit network interface and the switch only 10/100 mbit.

// Magnus

---

### Post by jrjvai on 2007-09-22
Ok, I took a look at the Samba guide but it didn't seem to be designed for Xubuntu. So it didn't take me anywhere. However, I previously followed some step by step guides for Samba (unfortunately this was a month ago so I can't find the urls anymore) and I think smb.conf should be alright. The result: it still doesn't show up on Windows.

I also tried using the pyNeighborhood on Xubuntu but the scan failed to find my laptop.

Second I tried WinSCP and tried to connect to [FONT="Fixedsys"]inet addr[/FONT] ifconfig gave me (on Xubuntu) but got "connection timed out".

---

### Post by jrjvai on 2007-09-22
Here is smb.conf:

```
[global]
    ; General server settings
    netbios name = KEPUINEN
    
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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
    path = /home/public/
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = vainio
    force group = vainio
available = no
browsable = yes
public = no
writable = no

```

---

### Post by ifconfig on 2007-09-22
> **jrjvai said:**
> Ok, I took a look at the Samba guide but it didn't seem to be designed for Xubuntu.

Well, it's written for Ubuntu but it will work exactley the same on Xubuntu.
The difference between Ubuntu and Xubuntu is that Ubuntu uses Gnome as default on the deskop, and Xubuntu Xfce.

If the share doesn't show up in Xp, you can right-click My computer and choose Map network drive. Then type \\YourIpaddress\YourShare. Or in the run dialog, \\YourIp.

// Magnus

---

### Post by ifconfig on 2007-09-22
There a sample configuration at this link,
[http://ubuntuforums.org/showpost.php?p=1125855&postcount=4](http://ubuntuforums.org/showpost.php?p=1125855&postcount=4)

In your smb.conf, in share part I would try change "available = no" to yes.

I haven't used Samba for a couple of years so I have no working smb.conf left.

// Magnus

---

### Post by vinutux on 2007-09-22
check wich is ur windows file system NTFS or FAT ........

fat not supported files larger than 2 gb....................:(

---

### Post by jrjvai on 2007-09-22
The filesystem is NTFS.

I enjoyed partial success. I guess changing available to yes did the trick. Now (in Windows) if in Network neighbourhood I click Show computers in the workgroup (these are my translations as my Windows is in Finnish) Samba 3.0.24(Kepuinen) shows up. I can't access it, however.

Right-clicking My computer and choosing connect to network drive... browsing for the directory results in the same thing: I can find the Xubuntu desktop but can't access it. I also tried writing the ip
```
\\62.183.217.16\home\public 
``` for the directory. But it can't be found. What's with the slashes? I mean Windows and Linux use it the other way round. So should it be / or \? I tried both though.

Was this the right ip? It is what the ifconfig command gave me for inet addr. Or should I use the numbers for bcast or Mask?

---

### Post by jrjvai on 2007-09-22
Setting up Samba is not exactly the same thing with Xubuntu and Ubuntu. For example it's not

System -> Administration -> Network 
but 
Applications -> System -> Network

This of course is a minor detail but it gets serious after that. In the General tab there is nothing about Windows networking. I couldn't find it in the Network settings at all.

---

