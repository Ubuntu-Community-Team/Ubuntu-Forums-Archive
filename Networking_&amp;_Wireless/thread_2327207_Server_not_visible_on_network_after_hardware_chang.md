---
title: "Server not visible on network after hardware change"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by Weidbrewer on 2016-06-08
I've had no end to my Samba troubles since I upgraded to 14.04, but recently I had to replace my mobo and CPU...now, I can't get it to work at all.  Before, even if I couldn't see the server shares on Windows, things like Android File Manager could still see them, but even that doesn't work now.  Remote applications that access via web sites (TeamSpeak, Calibre, Plex, etc) all still work.  I didn't change anything in my Samba config (attached) after the hardware change.

Any ideas?

---

### Post by bab1 on 2016-06-09
> **Weidbrewer said:**
> I've had no end to my Samba troubles since I upgraded to 14.04, but recently I had to replace my mobo and CPU...now, I can't get it to work at all.  Before, even if I couldn't see the server shares on Windows, things like Android File Manager could still see them, but even that doesn't work now.  Remote applications that access via web sites (TeamSpeak, Calibre, Plex, etc) all still work.  I didn't change anything in my Samba config (attached) after the hardware change.

Any ideas?
Looking over your last few threads and looking at the smb.conf file, my suggestion is to start over with configuring Samba (the file server) and the Linux file system.  The samba users (smbpasswd) should also be reviewed.

In the past you have used system-config-samba.  I myself and others have commented on that.  If you want to fix your problems you should learn how the system works and use a simple text editor to configure the shares.  Command line tools are all you need to prep the file system.  At the very most there is 1 hours worth of work.

There are several errors in the smb.conf file.  I think you should start with a fresh unmolested smb.conf file.  Do you have a backup copy?  Let me know if you want to start on this.


[COLOR="#0000CD"]Edit:  Your problems are not caused by upgrading to 14.04, but upgrading may have uncovered some misconfiguration.  I'm using the same smb.conf file that I used 8 years ago.  I have updated the minor deprecated parts, but the basic file (95%) is still the same one used on Samba3 and Samba4 file servers.[/COLOR]

---

