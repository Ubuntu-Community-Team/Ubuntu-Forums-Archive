---
title: "Samba printer sharing"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by mixepix on 2005-07-16
I've tried to share a printer on a samba server with an samba client. I can't get it to work though. I've tried the following. I have one script called *printsmb*
----------------------------
#!/bin/sh
/usr/bin/a2ps -o - | /usr/bin/smbclient //linux/printer -I 192.168.0.107 -U username%password -c ”print -”
------------------------------------

And then I put this in *printcap*

---------------------------------------------
smbprinter: \
	:sh:mx#0:of=/usr/local/lib/printsmb:\
	:lp=/dev/null:sd=/var/spool/smbprinter:lf=/var/log/lpd-errs:
-----------------------------------------------------------------------

If I try to print by typing "lpr -Psmbprinter* filename*" nothing happens. I can use the code in printsmb and print files from shell if I replace ”print -” with ”print *filename*”. The client is running Ubunto (It's not the default install though. I installed a mini ram version liked the one described in this [thread](http://www.ubuntuforums.org/showthread.php?t=42873&highlight=mini+ram) ) and the server Suse 9.3 

Any tips?

---

