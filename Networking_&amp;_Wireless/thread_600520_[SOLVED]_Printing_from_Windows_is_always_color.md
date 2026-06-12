---
title: "[SOLVED] Printing from Windows is always color"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by potam on 2007-11-02
Hello,

I have installed a HP Deskjet 3325 printer in Ubuntu 7.10. Printing from that computer is fine. But printing from a remote (somewhere in my home network) always uses just the color cartridge. Going to [http://localhost:631/admin/?op=set-printer-options&printer_name=deskjet_3320](http://localhost:631/admin/?op=set-printer-options&printer_name=deskjet_3320) the Resolution, Quality, Ink Type, Media Type is 600 dpi, color, black+color cartr. and printout mode is draft grayscale (black cartridge), so they seems to be fine. Again, printing from the Ubuntu computer is fine. Printing from another computer using Windows only the color cartridge is used. If I remove the color cartridge from the printer, nothing is printed. What is wrong, what sould I set?

My smb.conf is:
```

[global]
workgroup = MSHOME
server string = %h server (Samba, Ubuntu)
dns proxy = no
interfaces = 127.0.0.0/8 eth0
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
security = share
guest account = nobody
invalid users = root
printing = cups
printcap name = cups
socket options = TCP_NODELAY
wins support = no

[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
public = yes
create mode = 0700
guest ok = yes
use client driver = yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
ptintable = yes
public = yes
create mode = 0700

[share]
path = /home/potam/share
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes

```

---

### Post by potam on 2007-11-02
Problem solved. I had to install the HP printer in Windows as a postscript printer (Apple Color LW 12/660 PS). Everything is fine now when printing from a remote computer. Black is real black, not a mix of red green and blue.

---

