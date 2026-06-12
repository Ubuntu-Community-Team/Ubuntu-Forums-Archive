---
title: "Point upgrade to 18.04.1 broke samba"
date: 2018-08-20
forum: Networking &amp; Wireless
---

### Post by nequam on 2018-08-20
I had a working samba server.  Owing to a flurry of recent CVEs I did-release-upgrade.  Now I do not have a working samba server.

Previous upgrades have been entirely painless.  This one was slightly less so:  PHP somehow got disabled and php.ini got trashed.  However, there were no obvious problems reported (or logged) regarding samba, specifically.  And yet, my Windows 7 machine will no longer connect:  it says "Logon failure: unknown user name or bad password".  Nothing has changed at the Windows end.

I have checked smb.conf, but there is nothing obviously wrong with it.  (Of course, there wouldnt be - it was working perfectly before.)  I have also deleted and recreated the user, passwd, smbpasswd, service restart, reboot, everything.  Nothing in the logfiles.

Any ideas anyone?

---

