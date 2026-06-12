---
title: "Printer installation problem"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by Thomaz on 2016-02-10
Hi Guys,
I need to install a printer here, RICOH-C252DN
In Fedora was simple, I though in UBUNTU would be the same.
My SAMBA is running:
# smbstatus

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

# ps -ef|grep smb
porto     4057     1  0 Fev03 ?        00:00:00 /usr/lib/gvfs/gvfsd-smb-browse --spawner :1.1 /org/gtk/gvfs/exec_spaw/3
root     12721     1  0 13:49 ?        00:00:00 smbd -F
root     12812 12721  0 13:49 ?        00:00:00 smbd -F
root     16595 16583  0 16:48 pts/3    00:00:00 grep --color=auto smb


I added the printer after downloading the drivers.
I can reach the printer (ping).
It is all right , but when I try to print , he asks the password, and I type, but he asks again. In Fedora, I could print easily .
I tried a script downloaded from Ricoh site.
Ialso changed the user password to confirm it is correct, but none.
Someone has another guess to try ?
My UBUNTU is 14.04 .
Maybe starting Libreoffice (or other) by command line as root.
I also put the address in /etc/hosts file
Thanks,

---

### Post by Thomaz on 2016-02-10
I thought I have the answer.
I will test and post the results here tomorrow.
I don't know why worked easier in Fedora.
Someone has the answer ?
Thanks

---

### Post by HDTimeshifter on 2016-05-16
Did you get it to work? I was looking at buying a Ricoh SP C250DN, but it says it only supports Windows XP/Vista/7/8/Server 2003/2003R2/ 2008/2008R2/ 2012 (32 bit/64 bit) and later; Mac OS X 10.6 and later; Citrix MetaFrame.

---

