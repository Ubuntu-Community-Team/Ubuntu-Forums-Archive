---
title: "samba/cups/printing in windows issues"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by benighted on 2007-01-16
I've just had a bit of a go setting up our printer on an ubuntu machine and I ran into a problem or 2. 

Under windows, I can see the printer and add it as the default printer for my computer, but when it tries to download drivers from the ubuntu machine, it says the right drivers aren't there (and asks to install from a separate location). thats the first problem. Second is that once I install the drivers, the text beneath the name of the printer claims: "Access denied, unable to connect". (see attached)


even so, I can print a test page from the windows machine and that goes through fine, I decided to see if it would work printing anything, and it does seem to. all the while, windows still claims "Access denied, unable to connect". programs that I print from freeze for about 15s after I select print, then the printer does its job. 

is there something I've done wrong or not done? here are my config files for samba and cups that I've edited some, the samba config was mostly taken from this guide: [http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")
that samba config worked well for me, after trying to edit the sample config myself without much luck. 

Cups config file:
```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow 192.168.1.1
  Allow 192.168.1.3
  Allow 192.168.1.4
  Allow 192.168.1.5
  Allow 192.168.1.6
  Allow 192.168.1.7
  Allow 192.168.1.8
  Allow 192.168.1.9
  Allow 192.168.1.10
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

```

Samba config file:
```
[global]
    ; General server settings
    netbios name = server
    server string = %h (samba on ubuntu)
    workgroup = HOME
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
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[ubuntu_share]
    path = /mnt/data/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755

```

Edit: I should point out, the windows machine is windows XP, and ubuntu is 6.10, the printer is an epson CX6500 which uses a USB connection to the ubuntu machine.

Thanks, Ben.

---

### Post by gabspeck on 2007-01-28
I'm having the exact same problem -- I'd be very interested to see it fixed... :\

---

### Post by santo on 2007-02-04
Hi,

There are 2 things you can do:

a) remove the line
```

security = user

```

from the [global] section in /etc/samba/smb.conf

OR

b) create a user account on your ubuntu machine for each windows user that needs access to the printer(s)

cheers,


Santo

---

### Post by mobilehavoc on 2007-02-08
I tried removing the line about security = user and I still have the same problem described above except it doesn't even print for me. It just says Access denied - unable to connect.

Must be a permissions issue because I can bring up CUPS on port 631 in my browser and in windows I can point it to the HTTP address for the printer via CUPs and it seems to detect it...

Damm it - this is one of the last things I need to get working on Linux...really could use some help.

---

### Post by santo on 2007-02-11
Dit you try adding the user(s) to samba with the following command ?

```

sudo smbpasswd -a <username>

```

(Replace <username> with the real username of course ;-))

Hope that helps...

---

### Post by superjet on 2007-02-20
> **santo said:**
> Dit you try adding the user(s) to samba with the following command ?

```

sudo smbpasswd -a <username>

```

(Replace <username> with the real username of course ;-))

Hope that helps...


I don't know if it helped the orignal poster, but it sure helped me! I had to create an emergency print server with Knoppix and this was the missing command that made it smooth as silk!
 
Thank you very much!
 Jamie

---

### Post by airtonix on 2007-07-14
reason why you can use the cups via http is becuase the http does not require authentication like the samba does.

Now i have to fix windows network code.....damn thing keeps freezing for 30secs everytime i try to accss any windows share from any machine....ie not Ubuntu related

---

