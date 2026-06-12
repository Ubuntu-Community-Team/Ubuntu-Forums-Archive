---
title: "XBMC can't connect to Samba server"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by Qinx on 2007-12-07
Hi,

Since XP flipped me the finger again, I installed Ubuntu 7.10 two nights ago, now I'm trying to get samba up and running to share music and video's to my modded Xbox which runs XBMC. I followed the instructions on how to set this up in this thread:

[http://ubuntuforums.org/showthread.php?t=438577](http://ubuntuforums.org/showthread.php?t=438577)

But it doesn't work. I try to connect with XBMC to smb://xbox:xbox10@192.2.168.100/MyFiles. After a few seconds, it asks for a username and password. I did create a user "xbox" (with "xbox10" as password) in both Ubuntu AND on the Samba server. I can login to Ubuntu as user xbox. The dir that I intend to share does show up in the network shares app (System -> Administration -> Networkshares).

I first thought maybe there was a firewall issue (I don't know if Ubuntu has some default firewall mechanism after install), so I installed firestarter to see what was happening. When I tried to connect from XBMC, I saw the xbox's IP address pop up, so I allowed all traffic from it.

Since a colleague got the same setup to work with an older version of Ubuntu, I also tried his smb.conf file (of course adapted to reflect my system's settings), but that did not change anything.

Logging was not very helpful. When I try to connect with the XBOX, a file log.192.168.2.101 is created, but it's empty (0 bytes). 

Here's my smb.conf:

```

[global]
; General server settings
netbios name = stewie

workgroup = THUIS
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.2.1/150
interfaces = lo, eth0
bind interfaces only = true

hosts allow = 127.0.0.1, 192.168.2.101
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
syslog = 1

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[MyFiles]
path = /media/hda5
browsable = yes
valid users = xbox
read only = yes
guest ok = no
create mask = 0600
directory mask = 0700
force user = xbox
force group = xbox
available = yes
public = yes
;writable = no
;available = no
;public = no
public = no
writable = no

```

Does anyone have any suggestions what to do next? I mean, how difficult can it be...

TIA

---

### Post by Qinx on 2007-12-12
Okay, finally got it figured out. First there was a permissions issue where somehow, the /etc/samba directory had permissions set to 000. This must have been during install, but my colleague figured it can't be good, so we changed it to 755. 

This did not solve the problem with XBMC, it still could not connect. I was able to connect with a Windows 2000 laptop though. Only it took a hell of a long time to actually connect. Way much more time than XBMC - apparently - allows, so things looked like a time-out. Now I could have looked into how to increase the time-out in XBMC, but my colleague suggested something might be wrong with the DNS, since connecting through ssh, and even the smbclient -L localhost command took very long.

It turns out that the DNS in either my modem or my router (my colleague fixed it, and I'm not sure which one he meant) isn't working. He now adapted /etc/resolv.conf so that it doesn't use that dns anymore.

And now it works :-)

The only weird thing is that I tried to connect to Ubuntu's IP-address (192.168.2.100), not to it's name or something. Apparently, samba still needs to do some DNS lookup, but I do not know where. I could look into it, but as things are working now, I know myself well enough to know that I won't.

As I didn't see the dns as a possible problem in any of the samba sharing topics that I found with my search terms, I decided to post this problem/solution. Maybe it'll help someone else :-)

---

