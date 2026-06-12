---
title: "Help with auth.log message"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Kenzo on 2009-06-17
I'm geting the following messages in /var/log/auth.log when a session is opened by an ftp client accessing proftpd server.

Jun 17 21:52:48 server-desktop proftpd: pam_unix(proftpd:session): session opened for user video1 by (uid=0)
Jun 17 21:52:48 server-desktop proftpd: **pam_ck_connector(proftpd:session): cannot determine display-device**
Jun 17 21:52:48 server-desktop proftpd: pam_unix(proftpd:session): session closed for user video1 

Could someone shed some light on why the session is failing please?

---

### Post by Michael.Godawski on 2009-06-17
hi,

> **libpam-ck-connector**
ConsoleKit is a system daemon for tracking what users are logged
into the system and how they interact with the computer (e.g.
which keyboard and mouse they use).

This package provides a PAM module which can be used for console logins.
Graphical login managers should talk to ConsoleKit directly.

This is from Synaptics.

So perhaps it has something to do with different users and their rights?
But I am just guessing...

What strikes me as odd is that the display-device cannot be determined.

---

### Post by Kenzo on 2009-06-17
Thanks Michael. I'm almost certain its not user rights.  I can log in and upload files from a different FTP client using the same user (video1).
The FTP client with the problem is a DVR.  It is trying to send image files to the FTP server.  Logs in okay but then gets kicked out. The display-device part has me confused too.

Any other suggestions most welcome.

---

### Post by Kenzo on 2009-06-18
I've been thinking a bit more and maybe the error is occurring because the DVR doesn't have a display device like a 'normal' FTP client.  In fact there is no display device for the interaction between the DVR and the server.

So... how to get around the PAM and/or method (which I assume is GetDisplayDevice) that ConsoleKit is using for the user??

---

### Post by reverseturn on 2012-04-10
An old thread but I just had the same problem on 11.10 using ftp from a blackberry tablet. It would connect and just hang. Installed vsftpd instead of ftpd and ftp works fine.

---

### Post by CharlesA on 2012-04-10
> **reverseturn said:**
> An old thread but I just had the same problem on 11.10 using ftp from a blackberry tablet. It would connect and just hang. Installed vsftpd instead of ftpd and ftp works fine.
Please create a new thread instead of necroing an old one.

Thanks.

---

