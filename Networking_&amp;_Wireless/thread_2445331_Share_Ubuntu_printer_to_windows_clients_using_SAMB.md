---
title: "Share Ubuntu printer to windows clients using SAMBA"
date: 2020-06-12
forum: Networking &amp; Wireless
---

### Post by davehk on 2020-06-12
Hi,

I am trying to make printers connected to my Ubuntu 20.04 machine available to windows clients of several flavours - 2000, XP, 7 & 10. I'd also like to be able to browse for SMB shares on the ubuntu host from those clients ( I can connect to the shares by explicitly entering their details). I thought I'd done everything necessary - here are the relevant parts of smb.conf:

```
workgroup = WORKGROUP netbios name = namrok-i7 security = user proxy
   server min protocol = NT1
```

```
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 127.0.0.0/8 eno1
```

Note: I had to change eth0 to eno1 in the line above to match the output of ifconfig, before nmdb would start cleanly.

```
printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
;  use client driver = Yes
;   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = no
   guest ok = yes
```

I'm sure it's something simple I'm missing (it usually is!).

Thanks for any and all help.

---

### Post by TheFu on 2020-06-12
I think you meant to say you want to *make **printer drivers** available*, not printers.  Printers are already shared from Linux via CUPs through either lpr or IPP protocols. They just work, actually, and have just worked for over a decade. IPP is the easier protocol to use for any client I've seen.

Looks like a number of typos above where things that must be on separate lines, aren't. Perhaps fixing those would be the first step?
```
workgroup = WORKGROUP netbios name = namrok-i7 security = user proxy
```
should probably be:
```
workgroup = WORKGROUP 
netbios name = namrok-i7 
security = user 
```
I don't know if those are good or not, just commenting on the lack of netlines. The dangling "proxy" at the end - I haven't a clue about.

So, if you seek to have printer drivers available to Windows systems via samba and auto-installed, that is a different thing.  There is a guide to setup these things: 
[https://wiki.samba.org/index.php/Setting_up_Automatic_Printer_Driver_Downloads_for_Windows_Clients](https://wiki.samba.org/index.php/Setting_up_Automatic_Printer_Driver_Downloads_for_Windows_Clients)
There are many caveats. Anyway, how that link helps.

BTW, with Linux desktop clients, the last 10+ yrs, printing to a CUPS server running on Linux connected to printers has been really bonehead. Yesterday, I was using a Try Ubuntu Mate flash drive and wanted to print something.  Normally, connecting to a printer is bonehead - pick the driver, point at the network IPP URL ... print.  Yesterday, the printer was already setup after I "Browsed" the network for printers. It showed the alias and the correct printer name. LibreOffice --> Print just worked.  In my mind, it wasn't even a printer setup, it was just there already, preconfigured. Somehow.  From a flash drive Try Ubuntu environment that had been booted perhaps 45 minutes earlier.

---

### Post by davehk on 2020-06-12
Thanks for the suggestions - this is the first time I've had a problem since I first stared using Ubuntu 8.04. Up to now it's always been a doddle.

> I think you meant to say you want to make printer drivers available, not printers. 

sorry, but you think wrong. I meant  what I wrote. I cannot see the printers from my windows machines.

I didn't put this line in: 

```
workgroup = WORKGROUP netbios name = namrok-i7 security = user proxy
```

it was already there and if you split them the  way you suggest the daemons will not start.

 I don't need to download the driver from the Ubuntu server, as I have the windows drivers already on the clients (the same printers served from an Ubuntu 16.04 machine worked without a hitch).

---

### Post by davehk on 2020-06-12
OK, so I hadn't done this since I installed 16.04 4 years ago! I hadn't checked the "share printers" box on the CUPS server admin page. I knew it would be something simple, it always is!!

---

