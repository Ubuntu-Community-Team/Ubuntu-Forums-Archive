---
title: "Nautilus doesn't show workgroup (SAMBA)"
date: 2018-08-20
forum: Networking &amp; Wireless
---

### Post by konikoko on 2018-08-20
Hello,

I have a little problem with ubuntu (and also debian but it is the same problem I think).
I have 3 computers: Ubuntu, Debian and windows 7.
I installed samba and smbclient on the debian and the ubuntu. I also created a shared folder on both of them.
When I go on my windows 7, I can access both shares when I go to "network" and select the computer there.

I have one workgroup (named WORKGROUP) and all the computers have the same workgroup set but I can't see my workgroup in my "windows-network" folder on the ubuntu or the debian computer. On ubuntu the file manager I use is nautilus and on debian it is Thunar.
Both managers have a network tab with a "windows-network" directory. However when I click on this directory, the computer loads for a while and then it stops (finishes loading) and there is nothing in the directory. Normally there should be a WORKGROUP directory in the windows-network folder but there is nothing, on BOTH computers.

One strange thing I can do is access the shares with the following commands:
```

thunar smb://"""ip-here""" 
```
or 
```
nautilus smb://"""ip-here""" 
```

And when I type ```
smbtree
``` in the terminal, I can see the whole workgroup with all the computers.

Things I tried:

putting ```
client max protocol = NT1
``` in the smb.conf but it didn't change anything.

changing the netbios name to something with 15-letters or less (also in smb.conf)



Extra information: All the computers are connected with a switch (ethernet) but I think this doesn't really matter

Thanks in advance for reading and helping,

Konikoko

---

### Post by DuckHook on 2018-08-20
Welcome to the forums, Konikoko.

It has been literally years since I've worked with Windows networking or SMB (all the way back to XP) so my experience is so outdated that it is likely worthless, but I am responding because it seems that our usual network gurus seem to be busy.

At least with XP, it wasn't enough to install samba server and client in your Linux boxes. The problem with Windows workgroup sharing was that it used (note past tense) some weird peer-to-peer protocol; not a full-fledged DNS server. Unless you have some sort of separate DNS server—even a simple DHCP server like DNSMasq—Linux boxes won't be able to find things. DNSMasq (or similar) is usually available on most home routers. You may wish to turn this on. Alternatively, you can use one of your Linux boxes as a DNS server, though it would have to be left on all the time. This is the reason that most people leave this function to the router; it is permanently on by default.

The likely reason that you can see shares using your quoted commands is because you typed in the actual IP addresses. You don't need any sort of DNS lookup capability if you tell SMB exactly where the share is. Though unlikely, the switch may be a problem if it segments your traffic and doesn't let one segment peek at another.

Aside from these tidbits of obsolete knowledge, I'm afraid I won't be of much use to you. Hopefully, someone with proper networking and SMB knowledge will soon dive in here.

---

### Post by Morbius1 on 2018-08-21
** What version of Ubuntu are you using?

** What version of Samba are you using:
```
samba -V
```

** Please post the output of the following command:
```
testparm -s
```

---

### Post by konikoko on 2018-08-21
Thx for replying!
Here is the information you guys asked for:

Ubuntu Computer:

Version: 16.04.5

Samba version: 4.3.11-Ubuntu

result of testparm:

```


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
    netbios name = THINKPAD
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    client max protocol = NT1
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Share]
    path = /home/william/Share
    valid users = william
    read only = No
    guest ok = Yes

 
```

Debian computer:

version: Debian GNU/Linux 9.5 (stretch)

(for some strange reason, I can't use the samba -V command without sudo on the debian but I can on the ubuntu machine)
Samba version: Version 4.5.12-Debian

result of testparm command

```


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    netbios name = DEBIAN-WILLIAM
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    client max protocol = NT1
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Share]
    path = /home/william/Share
    guest ok = Yes
    read only = No
    valid users = william


```

---

### Post by Morbius1 on 2018-08-21
** "client max protocol = NT1" will do absolutely nothing on both your machines because it's already set to that. This is a Ubuntu 18.04 / samba 4.7xx thing. You can leave it or remove it - makes no difference.

** This would be a lot easier if you didn't have Win7 in the mix but my recommendation is to edit smb.conf again and add - right under the workgroup = WORKGROUP line another one:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
[I]I don't know that the commands are for Debian.
[/I]
The whole netbios process is a primitive mess so wait a few minutes and try to scan the network again.

** The two Linux boxes can use a more modern method ( and one Ubuntu 18.04 does by default ) of finding each other if you are interested:

On both Linux machines create a file at **/etc/avahi/services/samba.service**
And add this to it:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
Then restart avahi:
```
sudo service avahi-daemon restart
```
THe 2 Linux boxes should see each other as ***hostname* SMB **under Network- not under Windows Network[B].

[/B]Won't help with the Win7 box though.

---

### Post by konikoko on 2018-08-21
Thanks for your help Morbius1! I entered the line you gave me in the smb.conf file but it changed nothing (There is still nothing under the windows-network tab).
But I tried the modern method you gave me and it works! I can now see both linux boxes (under the network tab, exactly like you said). 
now the only thing left is browsing on the windows 7 box.

---

### Post by Morbius1 on 2018-08-22
> But I tried the modern method you gave me and it works! I can now see both linux boxes (under the network tab, exactly like you said).
If we could get Windows to join the avahi party 80% of the samba questions on this forum would disappear.

I will be honest. I'm having a hard time reconciling your observations:

> One strange thing I can do is access the shares with the following commands:
```
thunar smb://"""ip-here"""
```
That means samba itself - actual file sharing ( smbd ) if functioning correctly.
> And when I type
```
smbtree
```
in the terminal, I can see the whole workgroup with all the computers.
That means name resolution - discovering machines by netbios name ( nmbd ) is functioning correctly.

Samba is only made up of those two parts where Windows is concerned so I don't know what the issue is with doing this from the file manager. My first thought was a gvfs problem but your AskUbuntu post said you reinstalled gvfs-backends so it doesn't seem like that is the issue.

I'm at a loss at the moment. Just out of curiosity what happens when you run this command from the terminal on your Ubuntu machine using the correct host and share name:
```
gvfs-mount smb://win7-host-name/share-name
```
If it ran successfully it would just come back to the prompt and you should be able to access the share from your file manager. If not then it should give you an error message.

---

### Post by konikoko on 2018-08-22
Indeed it is a really strange problem. I used samba in the past and I never had a problem with it.
I tried the command and it works. After running it came back to the prompt and I could access the share from my file manager without any errors.
(It works for both debian and ubuntu)

Can it be a problem related to windows 7?

---

### Post by Morbius1 on 2018-08-22
If you can access the Win7 machine by it's name I don't see how Win7 could be the cause - at least I don't see how at the moment. I no longer have any Win7 machines here to test things on.

Until a reason for this is discovered I would suggest just access the machine by name in your file manager ( smb://win7-host-name ) and when it opens up to display the available shares - bookmark it. It will show up on the side panel when you need it and display the available shares.

---

