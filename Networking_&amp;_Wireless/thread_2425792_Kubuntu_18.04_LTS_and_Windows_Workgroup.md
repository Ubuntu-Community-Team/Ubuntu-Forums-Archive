---
title: "Kubuntu 18.04 LTS and Windows Workgroup"
date: 2019-08-30
forum: Networking &amp; Wireless
---

### Post by anthonyl2019 on 2019-08-30
Firstly I'm very new to Linux and once I have securely established networking with my other home computers I can start migrating systems.  Thus far any success I have is by stumbling on solutions and many posts I read do not seem quite applicable.

I have Windows XP, Windows 7 and a NAS and they happily can see each other and allow the transfer of files on my local LAN (mixture of wired and wireless) through the internet router, using IP 192.168.1.x.  I can also access these shares from my Android Smartphone.

Thus far I've setup my Kubuntu 18.04 LTS computer and I have the following successes and failures.

1) I can network to the XP machine but only if I stop then restart the Gufw firewall after a reboot.  

2) I have created a share on the Linux machine and can read the shared folder from the XP machines but I can't write to it.  

3) smbtree only works if I have the Firewall disabled.

I am using sudo smbstatus - Samba version 4.7.6-Ubuntu
and have amended 
/etc/samba/smb.conf
## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# 22/08/2019   workgroup = WORKGROUP
# DATAREVUE is the name of the Windows Workgroup
workgroup = DATAREVUE

#[https://forums.linuxmint.com/viewtopic.php?t=272334](https://forums.linuxmint.com/viewtopic.php?t=272334)
client max protocol = NT1

I seem to have a version of smb.conf in /usr/share/samba/ dated from May (before I installed Kubuntu)

The Linux shares have been setup simply via Dolphin and Properties of the folder.  The one I can read but not write to is /home/al/Documents which has:
Allow Guests, Everyone Full control. al ---  (I don't know what --- means)

The Linux share I can't get to (that is when things are working) is /media/al/Shared partition/Lenovo Moved Folders
I get to being asked the User Name and Password and I'm entering my machine login credentials which are not accepted.  The share is setup Do not allow Guests, Everyone Read only, al Full Control

The firewall is setup as follows though I'm not happy with it as I'd rather it be restricted to my LAN IP address range:
```

 sudo ufw status 
[sudo] password for al: 
Status: active

To                         Action      From
--                         ------      ----
137,138/udp                ALLOW       Anywhere                  
139,445/tcp                ALLOW       Anywhere                  
137,138/udp (v6)           ALLOW       Anywhere (v6)             
139,445/tcp (v6)           ALLOW       Anywhere (v6)             

137,138/udp                ALLOW OUT   Anywhere                  
139,445/tcp                ALLOW OUT   Anywhere                  
137,138/udp (v6)           ALLOW OUT   Anywhere (v6)             
139,445/tcp (v6)           ALLOW OUT   Anywhere (v6)             

```

Having got so near I'm reluctant to stumble further without guidance though it may be just as well to know what I should backup before making further changes.

Thank you.

---

### Post by SeijiSensei on 2019-08-30
> I get to being asked the User Name and Password and I'm entering my machine login credentials which are not accepted. 

Try creating a Samba account using smbpasswd.  

```
sudo smbpasswd -a al
```

You can use the same password as you use for the system itself, or an entirely different password.

---

### Post by Morbius1 on 2019-08-30
I'm telling you up front that I do not use KDE so this is more of a generic samba response to your questions:
>  1) I can network to the XP machine but only if I stop then restart the Gufw firewall after a reboot.  
Allowing samba through the firewall ( which I also don't use ) should have been sufficient:
```
sudo ufw allow Samba
```
[COLOR=#0000cd]**EDIT**[/COLOR]: Um ... that may not be sufficient. Your Windows versions are using the old smb ports and there is something you may need to do to iptables: [https://askubuntu.com/questions/875845/kernel-4-8-ufw-and-smb-not-working-together](https://askubuntu.com/questions/875845/kernel-4-8-ufw-and-smb-not-working-together)
> 2) I have created a share on the Linux machine and can read the shared folder from the XP machines but I can't write to it.  
The Linux share I can't get to (that is when things are working) is /media/al/Shared partition/Lenovo Moved Folders
Edit /etc/samba/smb.conf and add a line under the workgroup = DATAREVUE line:
```
force user = al
```
Save the file then restart smbd:
```
sudo service smbd restart
```
> I get to being asked the User Name and Password and I'm entering my  machine login credentials which are not accepted.  The share is setup Do  not allow Guests, Everyone Read only, al Full Control

Did you add al to the samba password database:
```
sudo smbpasswd -a al
```
>  The firewall is setup as follows though I'm not happy with it as I'd rather it be restricted to my LAN IP address range:
There is probably a very elegant way to do this in gufw but since I don't use a firewall you can do this in samba itself if you are interested:
Edit /etc/samba/smb.conf again and below the force user line add this one:
```
hosts allow = 192.168.1.
```
Don't forget that last period (.) at the end.

Then restart smbd again.

Should you have further issues posting the output of the following commands will let folks here know how you are set up:
```
testparm -s
net usershare info --long
```

---

### Post by SeijiSensei on 2019-08-30
Like Morbius, I don't use a firewall on ordinary client machines and never have.  I use firewalls on Internet-facing servers or gateways, but that's it. 

I'd turn gufw off entirely myself.  You must have installed gufw separately because none of my KDE machines have ever run a firewall by default.  It's not part of the default Kubuntu installation.

---

### Post by anthonyl2019 on 2019-08-30
I'll investigate the above though I'll add that for a while I was running Mint KDE and had it all working more or less straight out of the box with their implementation.  The only reason I've changed is that Mint KDE is coming to end of life and I messed the whole system up by taking advice from another forum probably for a different Linux which is why I'm being more careful.

The folder properties show: "Share with Samba (Microsoft Windows)" and I understand that it wouldn't if Samba wasn't recognised.

The outputs requested are:
```

al@al-HP-EliteBook-8440p:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

# Global parameters
[global]
        client max protocol = NT1
        dns proxy = No
        log file = /var/log/samba/log.%m
        map to guest = Bad User
        max log size = 1000
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server string = %h server (Samba, Ubuntu)
        syslog = 0
        usershare allow guests = Yes
        workgroup = DATAREVUE
        idmap config * : backend = tdb


[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```



```

al@al-HP-EliteBook-8440p:~$ net usershare info --long
[Home Documents]
path=/home/al/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Lenovo Moved]
path=/media/al/Shared partition/Lenovo Moved Folders
comment=
usershare_acl=Everyone:R,Unix User\al:F,
guest_ok=n
```

---

### Post by SeijiSensei on 2019-08-30
Start with adding your user with smbpasswd.  I suspect that will cure a lot of problems.  Also I'd fix this:

> WARNING: The 'netbios name' is too long (max. 15 chars).

Add a "netbios name = SOMENAME" entry to the [global] section.

Does the computer have a Unix hostname?  What does the "hostname" command return?  Usually I try to match the Unix hostname and netbios name.  Don't include any domain parts, like "hostname.example.com."  Just use "hostname."

---

### Post by anthonyl2019 on 2019-08-30
The hostname is: al-HP-EliteBook-8440p
Windows sees it as al-HP-EliteBook
It was "given" to me when I set the machine up, though HP-EliteBook-8440p is what the laptop is
If I create a new share on the al-HP-EliteBook-8440p it immediately shows up on my Windows machine as al-HP-EliteBook
I don't think this is where the problem is - it is a rights/permissions issue on the folder I'm sharing I feel.

---

### Post by anthonyl2019 on 2019-08-30
> **SeijiSensei said:**
> Like Morbius, I don't use a firewall on ordinary client machines and never have.  I use firewalls on Internet-facing servers or gateways, but that's it. 

I'd turn gufw off entirely myself.  You must have installed gufw separately because none of my KDE machines have ever run a firewall by default.  It's not part of the default Kubuntu installation.

Yes I installed the Gufw.  I've always had Firewalls on my Windows machines, though after further thought I've realised that I totally allow the LAN and what I specifically allow/block is software so if anything tries to go out that I've not allowed it flags, and of course Gufw is not doing that.  As I'm on a NAT behind my router there is probably little point in bothering with the firewall and I'll see if I can remove it, or at least simply leave it turned off.

---

### Post by anthonyl2019 on 2019-08-31
I'm still stuck.  I can't get to a situation where I have permissions to write to the Linux folder from Windows.  If I set up a username I can't log in.  I've created the shares within Samba and followed the section at the end of 
[https://www.techrepublic.com/article/how-to-set-up-quick-and-easy-file-sharing-with-samba/](https://www.techrepublic.com/article/how-to-set-up-quick-and-easy-file-sharing-with-samba/)
so I can see the share from Windows but if I use the option to have a username as per example the login screen from Windows will not accept the credentials.  If I allow anyone then I can see/read the contents but can't write to the folder.  The shares show up immediately I have done the changes in Linux, either through Dolphin (Properties) or smb.conf - after smbd restart.

---

### Post by Morbius1 on 2019-08-31
You stated before that you used Mint KDE which worked. It looks like the last Mint KDE was based on Ubuntu 16.04 so you are going to have to dumb down Kubuntu 18.04 to allow WinXp ( and maybe Win7 ) access by adding the following under the same workgroup line as the others:
```
lanman auth = yes
ntlm auth = yes
```
I'm not sure a restart of smbd is going to be enough. You may need to reboot the Kubuntu box.

You followed a HowTo that has you add share definitions to smb.conf directly so now you have samba shares created 2 different ways in two different configuration files. You need to post the output of the [highlight] net usershare info --long[/highlight] and [highlight] testparm -s [/highlight] commands again to see if they conflict.

---

### Post by anthonyl2019 on 2019-08-31
1) I've put the two "auth" lines into smb.conf
2) I've changed the Netbios name to HPLINUX, and when that made no difference I changed the HOSTS and HOSTNAME files to match, to no avail.

To reiterate, everything works except the ability to write to the Linux machine, ie I can make it read and I can read/write from the Linux machine to any of my other devices.  We're missing something basic and probably with permissions. 

The outputs now are:
```

al@hplinux:~$ net usershare info --long 
[Documents]
path=/home/al/Documents
comment=
usershare_acl=Everyone:F,HPLINUX\shares:F,HPLINUX\al:F,
guest_ok=y

[Downloads]
path=/home/al/Downloads
comment=
usershare_acl=Everyone:R,HPLINUX\shares:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/lenovo moved is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```
**Note the last folder error is just further testing and unless relevant can be ignored for the purposes of this thread
```

al@hplinux:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Processing section "[share1]"
Processing section "[SECURED]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    client max protocol = NT1
    dns proxy = No
    lanman auth = Yes
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    ntlm auth = ntlmv1-permitted
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    usershare allow guests = Yes
    workgroup = DATAREVUE
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[public]
    comment = Public Share
    force user = nobody
    path = /home/al/Documents
    read only = No


[share1]
    comment = A Shared Directory
    force user = nobody
    path = /home/al/Documents
    read only = No


[SECURED]
    path = /samba/shares
    read only = No
    valid users = @smbgrp

```

** I'm ending up with too many tests!  But each time I amend smb.conf and reset it shows up on the Windows machine.

---

### Post by Morbius1 on 2019-08-31
> [public]
    comment = Public Share
    force user = nobody
    path = /home/al/Documents
    read only = No
That makes no sense. That is a share that requires credentials to access but when the remote user passes the correct credentials his identity will change to "nobody". Even if "nobody" had write access to the folder ( which would only happen if you ran [highlight]chmod 777 /home/al/Documents[/highlight] ) anything saved would be owned by nobody and al wouldn't be able to do anything with it.

Add this under the workgroup line as I suggested originally:
```
force user = al
```
And change the example share definition to this:
> [public]
    comment = Public Share
    [COLOR=#0000cd]**force user = al**[/COLOR]
    path = /home/al/Documents
    read only = No
THen restart smbd again.

---

### Post by coffeecat on 2019-08-31
@anthonyl2019, I've added BBCode code tags to three of your posts. You'll see that has restored the columnar formatting that was lost by posting it as ordinary text in the bode of the post. The forum software strips out adjacent spaces unless they are enclosed in code tags. When posting terminal output or the contents of config files, please use code tags.

There's a link in my sig to a guide for using code tags should you need it.

Thanks.

---

### Post by anthonyl2019 on 2019-08-31
> **Morbius1 said:**
> That makes no sense. That is a share that requires credentials to access but when the remote user passes the correct credentials his identity will change to "nobody". Even if "nobody" had write access to the folder ( which would only happen if you ran [highlight]chmod 777 /home/al/Documents[/highlight] ) anything saved would be owned by nobody and al wouldn't be able to do anything with it.

Add this under the workgroup line as I suggested originally:
```
force user = al
```
And change the example share definition to this:

THen restart smbd again.

Well I'm afraid at this stage a lot of it doesn't make sense to me despite having successfully setup and installed Novell networks (from v2 to v4), Windows NotWorking from (3.x) and my own little LAN at home now I'm retired so I'm at the mercy of what I find on various forums.

However, thank you very much because I now have read/write access to the Public folder and I'll go through the exercise of tidying up the mess I've created and probably setting my host/hostname back again.

If I had wanted to have a login to a folder from Windows to Linux what should I now do?

---

### Post by SeijiSensei on 2019-08-31
Adding an entry to /etc/fstab will permanently mount the Windows shares.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

You'll need to install the cifs-utils package.

---

### Post by anthonyl2019 on 2019-09-03
> **SeijiSensei said:**
> Adding an entry to /etc/fstab will permanently mount the Windows shares.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

You'll need to install the cifs-utils package.

Thanks, but that is looking at it the wrong way, I'm trying to see Linux from WIndows not Windows from Linux (which has never been a problem).

However I will bear that in mind though I'm wary of having too many packages installed.

---

### Post by anthonyl2019 on 2019-09-03
> **anthonyl2019 said:**
> 
However, thank you very much because I now have read/write access to the Public folder and I'll go through the exercise of tidying up the mess I've created and probably setting my host/hostname back again.

If I had wanted to have a login to a folder from Windows to Linux what should I now do?

I now have it all working as I wish though I don't exactly know how, but I will share what bit of knowledge I have:

1) The Dolphin file manager allows the Properties of a folder to be changed to make it Shareable to Windows.  This creates an entry in 
/var/lib/samba/usershares/ for that sharename and Windows 7 can log into that share but XP cannot

2) I've amended smb.conf, in part with the suggestions from here and in truth I do not know which bits make it work and which bits are redundant so good luck if you are trying it yourself but the result is that I am asked to login and I use my username/smbpassword.  The desired folders are NOT shared through the file manager.  
I've cleaned up hosts (simply localhost for ip4)  and hostname hplinux

The key entries as far as I understand are, where 'al' is me as the user:

```
#31.08.19 try shorter netbios name
netbios name = hplinux

#31.08.19 from thread
    lanman auth = yes
    ntlm auth = yes
    force user = al
    workgroup = DATAREVUE
    Client Max protocol = NT1

and I've commented out:

#al 3.9.19   passdb backend = tdbsam
#al 3.9.19  obey pam restrictions = yes

[home]
comment = al Docs
path = /home/al/Documents
force user = al
read only = No 
writable = yes

```

New folders can be added quite readily and it seems that smb.conf does not need to be restarted for them to take effect, they are there immediate.

I'll now mark this thread as [SOLVED] and move on to the next steps of my conversion from Windows to Linux.  See you on another forum/board/post.

---

