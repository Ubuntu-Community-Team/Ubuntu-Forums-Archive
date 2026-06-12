---
title: "Set up Samba, but can't see Windows shares under MSHOME"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by me1on on 2007-12-02
I recently installed/set up Samba according to [this guide]("http://ubuntuforums.org/showthread.php?t=202605"), but I have a problem.  When I type smb:/ in Konqueror (yes, I'm using KDE), the "Mshome" workgroup shows up. When I click "Mshome," the only thing that I can see is my Linux box (named "Me1on"). My Windows share doesn't show up under Mshome. When I try to access it directly (smb://192.168.1.131) it works. Typing smb://Mshome/192.168.1.131 doesn't. My question is: How can I get my Windows computer to show up under the Mshome workgroup? I've disabled the firewalls on my Ubuntu box (Firestarter) and my Windows box (Norton), and I can access the shares on my Ubuntu box perfectly fine from my Windows box. 

Does anyone else have this problem? I suppose I could just access it directly when I need to, but sometimes, like when setting up a SMB printer in KDE, I need to be able to see the Windows box under the MSHOME workgroup.

Here's my smb.conf:
```

[global]
; General server settings
netbios name = me1on
server string = 
workgroup = Mshome
announce version = 5.0
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 
interfaces = lo, eth0
bind interfaces only = yes

passdb backend = tdbsam
null passwords = yes
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto

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
guest ok = yes
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
path = /home/shared/
read only = no
create mask = 0644
force user = john
force group = john

```

---

### Post by Mular on 2007-12-12
Well I too am having this same problem. From what I gather from other threads about this sorta issue.. 

If you can access your share by doing smb://192.168.1.102 or whatever, its not your ubuntu config.. I guess to maybe it has to do with windows just being slow to report the network neighbors.. But ya my problem is yours exactly.. 

The whole thing just is kinda lousy, I don't blame ubuntu I think its just a windows thing because I have never thought the networking in windows was fast in anyway. 

I have never waited to see if the network shows up after a bit.. Maybe leave both computers on, access the window share via smb://192.168.x.xxx .. then check network:// later and see if it shows up?

---

