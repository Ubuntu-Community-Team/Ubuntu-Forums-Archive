---
title: "Help needed with Smartmon tools"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-28
I am trying to get info on my hard disk(as recommended by Audiomick,thanks again!)
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
and I'm having difficulty(what's new?) with the first stages.
I have enabled S.M.A.R.T. in BIOS.
pasted:
To ensure that your drive supports SMART, type: 
smartctl -i /dev/sda 
=result in terminal:
computer@computer-desktop:~$ smartctl -s on /dev/sda 
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sda failed: Permission denied
computer@computer-desktop:~$ 

I'll attach a shot of the HD:
Thanks again again
EDIT:the result of my HD's smartmon
 Device Model:     WDC WD5000AACS-00G8B1
Serial Number:    WD-WCAUK0106989
Firmware Version: 05.04C05
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 28 23:34:20 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

### Post by jerrrys on 2010-03-28
go to your **disk utility** in system>admin and see if it reads your drive

[ATTACH]151700[/ATTACH]

---

### Post by MisFitt on 2010-03-28
Thanks,btw I'm using jaunty but going to have a go at installing palimpsest anyway-yes?

---

