---
title: "Desperately seeking printing under VMWare"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by grkuntzmd on 2008-05-08
I am running Ubuntu Hardy x64 as my VMWare 6 host on a Dell Inspiron 1720. I have Vista Home Premium running under VMWare as a guest. I have cups configured in the Linux host and can print to my Brother HL-5140 without any problems from the Linux host.

I cannot get Vista to print to it. I have Googled every combination of terms that I can think of.

My VMWare session has the host on vmnet1 at 192.168.6.1 and the guest at 192.168.6.2 (static IPs). I can ssh into the host from the guest and I ran nmap (zenmap from nmap.org -- great program) under Windoze and port 631 is open on the host.

I have tried "naked" cups printing using the URL
```
http://192.168.6.1:631/printers/HL-5140_series
```
but get an error in Vista: "Windows cannot connect to the printer. Make sure that you have typed the name correctly, and that the printer is connected to the network."

I have tried samba printing and can see the printer from Vista, but when I try to send a test page, I get the error "access denied" in the printer control panel.

Any ideas? I am at my wits end.

BTW, I can print from Vista to a nearby network printer using LPD (linksys or dlink print server).

Thanks, Ralph

cupsd.conf:
================================================================
```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
Listen *:631
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Deny From All
  Allow From 127.0.0.1
  Allow From 192.168.6.*
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

smb.conf:
================================================================
```

[global]
;General server settings
netbios name = Cerberus
workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
wins support = yes

interfaces = vmnet1 vmnet8
bind interfaces only = true

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

; NOTE: Inside this place you may build a printer driver repository for Windows 
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

;[printers]
;path = /var/spool/samba
;printable = yes
;guest ok = yes
;browseable = no
;read only = no
;use client driver = yes

[hl-5140]
comment = HL-5140_series
path = /var/spool/samba
read only = no
guest ok = yes
printable = yes
printer name = HL-5140
use client driver = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

```

---

