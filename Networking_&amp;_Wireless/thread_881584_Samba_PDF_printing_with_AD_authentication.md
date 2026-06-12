---
title: "Samba PDF printing with AD authentication"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by inselaffe on 2008-08-06
I've set up a server which shares out the cups-pdf printer, which outputs a PDF to a folder the user can grab from a samba share.

All users who print are interpreted as "anonymous" so their PDFs end up in the same folder. I want to take this a stage further. The users are members of an Active Directory domain. I'd like each user's PDFs to end up in a different folder such as their home share.

I imagine this requires at least a couple things:
1. The samba server to use active directory to authenticate the users.
2. Cups-pdf to "recieve" the user authentication so it can work out where to save its output.

I've used likewise-open successfully for user logons on machines but I've not managed to get it to work with samba. I've tried it the old-fashioned way, although admittedly not recently and not with this specific aim in mind, but never got much success with that (things like different machines assigning different uids to the same user broke too many things to be useful).

This strikes me as something that fits into the category of so useful someone must be doing it already, so any tips?

Here's a couple of posts I found which look like there are along these lines, but both come to the conclusion that likewise-open with samba doesn't work, but don't give a alternative (in simple enough terms).
[http://ubuntuforums.org/showthread.php?t=761464](http://ubuntuforums.org/showthread.php?t=761464)
[http://ubuntuforums.org/showthread.php?t=835056](http://ubuntuforums.org/showthread.php?t=835056)

---

### Post by inselaffe on 2008-08-08
Well here's a *mostly* working solution. It provides a network shared printer which Windows users can connect to. They print to it, and a PDF is created in a personal folder within one of their existing network drives.

I didn't use likewise-open for this. The samba etc config files are below. There were a few more steps involved here around providing the Windows to Windows clients, and getting app-armor to behave. Once the remaining couple issues are resolved I may write this as a guide if it's useful to anyone.

**However it's not quite there; there are a couple of issues to be resolved for this to be complete.**
[LIST=1]
[*]The first print job a user makes creates the user's folder, but does not create the PDF. Subsequent prints create PDFs in that folder.
[*]No NTFS permissions are set on the user folders to restrict access to other users. I'm not sure yet how to go about this.
[/LIST]

This is logged in /var/log/cups/cups-pdf_log on a first print, where the folder gets created but the PDF does not:
```
Fri Aug  8 16:36:22 2008  [DEBUG] switching to new gid (lpadmin)
Fri Aug  8 16:36:22 2008  [DEBUG] initialization finished (v2.4.6)
Fri Aug  8 16:36:22 2008  [DEBUG] user identified (DOMAIN\testuser)
Fri Aug  8 16:36:22 2008  [DEBUG] output directory name generated (/data/pdf/print/testuser)
Fri Aug  8 16:36:22 2008  [DEBUG] spoolfile name created (/var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] source stream ready
Fri Aug  8 16:36:22 2008  [DEBUG] destination stream ready (/var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] owner set for spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] found beginning of postscript code (%!PS-Adobe-3.0)
Fri Aug  8 16:36:22 2008  [DEBUG] now extracting postscript code
Fri Aug  8 16:36:22 2008  [DEBUG] found title in ps code (PBX Changes.xlsx)
Fri Aug  8 16:36:22 2008  [DEBUG] found end of postscript code (%%EOF)
Fri Aug  8 16:36:22 2008  [DEBUG] all data written to spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] trying to use PS title (PBX Changes.xlsx)
Fri Aug  8 16:36:22 2008  [DEBUG] removing trailing newlines from title (PBX Changes.xlsx)
Fri Aug  8 16:36:22 2008  [DEBUG] removing special characters from title (PBX Changes.xlsx)
Fri Aug  8 16:36:22 2008  [DEBUG] title successfully retrieved (PBX_Changes_xlsx)
Fri Aug  8 16:36:22 2008  [DEBUG] input data read from stdin
Fri Aug  8 16:36:22 2008  [DEBUG] output filename created (/data/pdf/print/testuser/PBX_Changes_xlsx.pdf)
Fri Aug  8 16:36:22 2008  [DEBUG] ghostscript commandline built (/usr/bin/gs -q -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="/data/pdf/print/testuser/PBX_Changes_xlsx.pdf" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f /var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] output file unlinked (/data/pdf/print/testuser/PBX_Changes_xlsx.pdf)
Fri Aug  8 16:36:22 2008  [DEBUG] TMPDIR set for GhostScript (/var/tmp)
Fri Aug  8 16:36:22 2008  [DEBUG] entering child process
Fri Aug  8 16:36:22 2008  [DEBUG] GID set for current user
Fri Aug  8 16:36:22 2008  [DEBUG] UID set for current user (DOMAIN\testuser)
Fri Aug  8 16:36:22 2008  [STATUS] directory created (/data/pdf/print/testuser)
Fri Aug  8 16:36:22 2008  [DEBUG] failed to set owner on directory (non fatal) (/data/pdf/print/testuser)
Fri Aug  8 16:36:22 2008  [ERROR] failed to set mode on user output directory (/data/pdf/print/testuser)
Fri Aug  8 16:36:22 2008  [DEBUG] ERRNO: 1
Fri Aug  8 16:36:22 2008  [DEBUG] waiting for child to exit
Fri Aug  8 16:36:22 2008  [DEBUG] spoolfile unlinked (/var/spool/cups-pdf/SPOOL/cups2pdf-6806)
Fri Aug  8 16:36:22 2008  [DEBUG] all memory has been freed
Fri Aug  8 16:36:22 2008  [STATUS] PDF creation successfully finished (DOMAIN\testuser)

```

The error *[ERROR] failed to set mode on user output directory (/data/pdf/print/testuser)* occurs regardless of whether apparmor is in complain or enforce mode. On a subsequent print, where a PDF is created in the folder, this is logged: * [ERROR] failed to set file mode for PDF file (non fatal) (/data/pdf/print/testuser/Test_Page.pdf)*.

Any thoughts, anyone? Is aa be the culprit or is that a red herring?

**Only configs follow**
/etc/krb5.conf:
```
[logging]
	default = FILE:/var/log/krb5.log
	kdc = FILE:/var/log/krb5kdc.log
	admin_server = FILE:/var/log/kadmin.log

[libdefaults]
	default_realm = DOMAIN.NET
	dns_lookup_realm  = false
	dns_lookup_kdc = true

[appdefaults]
	pam = {
	debug = false
	ticket_lifetime = 36000
	renew_lifetime = 36000
	forwardable = true
	krb4_convert = false
	}
```

/usr/share/pam/common-account:
```
account	required	pam_unix.so
```

/usr/share/pam/common-auth:
```
auth	required	pam_env.so
auth	required	pam_unix.so
```

/usr/share/pam/common-password:
```
password sufficient pam_winbind.so
password required pam_unix.so nullok obscure min=4 max=8 md5
```

/usr/share/pam/common-session:
```
session	required	pam_limits.so
session	required	pam_unix.so
```

/etc/samba/smb.conf
```
[global]
workgroup = DOMAIN
realm = DOMAIN.NET
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = ADS
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
invalid users = root
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
socket options = TCP_NODELAY
domain master = no
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
winbind enum groups = yes
winbind enum users = yes
usershare allow guests = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @"DOMAIN\domain admins"
#Test share
[testshare]
comment = Test share
read only = no
path = /data/test
valid users = @"DOMAIN\domain users"
```

/etc/cups/cups-pdf.conf:
```
Out /data/pdf/print/${USER} #a smb share on a Win2003 server is mounted at /data/pdf
Grp lpadmin
UserPrefix DOMAIN\ #Plain username is received, we need the domain prepended
LogType 7
```

/etc/nsswitch.conf
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns wins
networks:       files dns

protocols:      files
services:       files
ethers:         files
rpc:            files

netgroup:       files
publickey:	nisplus
automount:	files
aliases:	files nisplus
```

/etc/apparmor.d/usr.sbin.cupsd:
```
# vim:syntax=apparmor
#include <tunables/global>
[...]
  /bin/dash ixr,
  /bin/bash ixr,
  /etc/papersize r,
  /etc/cups/cups-pdf.conf r,
  @{HOME}/PDF/ rw,
  @{HOME}/PDF/* rw,
  /data/pdf/print/ rw,
  /data/pdf/print/** rw,
  /usr/bin/gs ixr,
  /usr/lib/cups/backend/cups-pdf mr,
  /usr/lib/ghostscript/** mr,
  /usr/share/** r,
  /var/log/cups/cups-pdf_log w,
  /var/spool/cups-pdf/** rw,
}
```

---

### Post by HuntMike79 on 2009-02-13
I'm trying the exact same thing as you, so far I can only send a test page from a Windows XP box that produces a PDF in the Anonymous folder...

I'll post again when I've made some progress! ;)

Have you tried this in Hardy?

---

