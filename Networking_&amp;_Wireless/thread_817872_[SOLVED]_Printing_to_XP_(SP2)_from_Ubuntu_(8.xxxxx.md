---
title: "[SOLVED] Printing to XP (SP2) from Ubuntu (8.xxxxx)"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by drdoug8356 on 2008-06-04
This driving me nuts....
I'm trying to use a XP workstation a printer attached for my default printer from Ubuntu. Have Samba installed. When I go to add a printer, nothing shows up. So I go to "Windows printer via SAMBA and under SMB Printer I select Browse. The workgroup comes back, and under the workgroup, the Ubuntu box shows up but not the the window boxes, let alone any printers. I also have file sharing setup under SAMBA so the windows box can see directories on the Ubuntu box. This works fine. I'm really begin to think something is not setup correctly in windows. See smb.conf below as I am using.

#
# Configurationn file for Workgroup dcco.
#
#
[global]
workgroup = dcco
netbios name = dcco-media
security = share
printcap name = cps
show add printer wizard = No
printing = cups
load printers = Yes

; [printers]
; comment = default printer
; path = /var/spool/samba
; guest ok = Yes
; printable = Yes
; use client driver = Yes
; browsable = No

[data]
comment = data
path = /home
read only = No
guest ok = Yes

Any help is GREATLY APPRECIATED

drdoug

---

