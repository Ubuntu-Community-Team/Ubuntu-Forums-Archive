---
title: "Windows can't access SMB shares on Ubuntu"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by renatosilva on 2007-10-10
Me and my colleague are trying to make a Windows (SMB) share on a Ubuntu machine we intend to use as a file server.

Another Ubuntu workstation can access normally the shares, but not the Windows ones. When I type \\hostname to see the shares available, then Windows ask me for a user and password. We tried all accounts available on bthe target machine, also in formats like user@IP, user@hostname, hostname\user etc. but nothing works.

We also searched for authentication configs on the related menus but we didn't find anyone. My theory is that we have to configure authentication on the shares, but Ubuntu seems not to make it available for us, specifically it seems not to bring up SAMBA options to the "high-level".

Please help us.

---

### Post by helgman on 2007-10-10
Do you hava SAMBA user?

If the answer is no, investigate **man smbpasswd** for more information.

Else if the answer is yes ... hrm. Are you using a server or desktop version of Ubuntu?

---

### Post by renatosilva on 2007-10-10
I discoevred that SAMBA has its own users database which logins have to match the existing system users. So we made #smbpasswd -a #existing-system-user for the user we were trying to log-in with. 

However, this is a little weird don't? Does somebody can explain me why? Windows autenticates access requests for shares directly against the system users instead of a separated database. 

Also, as Ubuntu clients had access to the shares, it suggests that there exist a kind of default user password which is obviously unknown by Windows, and by us either. Does anyone?

Another point is that it seems not to exist any interface for configuring share permissions, which is annoying and not human-friendly, in my opinion. 

Also, strangely after this my Windows got access to the shares without that logon promt, maybe the already-typed login/passwords were in cache and Windows used them automatically, which worked this time.

---

### Post by helgman on 2007-10-10
> **renatosilva said:**
> However, this is a little weird don't? Does somebody can explain me why? Windows autenticates access requests for shares directly against the system users instead of a separated database.

Quote from [The Official Samba 3.2.x HOWTO and Reference Guide](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html) chapter 11:

*Many people ask why Samba cannot simply use the UNIX password database. Windows requires passwords that are encrypted in its own format. The UNIX passwords can't be converted to UNIX-style encrypted passwords. Because of that, you can't use the standard UNIX user database, and you have to store the LanMan and NT hashes somewhere else.*

> Also, as Ubuntu clients had access to the shares, it suggests that there exist a kind of default user password which is obviously unknown by Windows, and by us either. Does anyone?

It might have something to do with SID (Windows) where some are "well known" (such as Administrators (s-1-5-32-544) or Anonymous (s-1-5-7)) where as Linux users have a UID (such as root (1) and so on). As you see there is a big difference between the SID and UID. I'm sure some research could provide you with an answer.

> Another point is that it seems not to exist any interface for configuring share permissions, which is annoying and not human-friendly, in my opinion.

Such as the security tab in Windows? This might have something to do with the difference between Linux and Windows. Once again the [documentation](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id374666) can give some background/information. I guess user friendly depends on what you are use to? But sure, coming from Windows I definitely understand your point. 

> Also, strangely after this my Windows got access to the shares without that logon promt, maybe the already-typed login/passwords were in cache and Windows used them automatically, which worked this time.

Nothing strange here. When you Windows machine authenticates with the server they agree at the Windows machine and user should have access. This is then stored for a period of time so that you won't have to re-authenticate every time you do something (it uses your old credentials). Given time or if you reboot - you should have to authenticate again (if you didn't store the username/password). The same thing should happen if you connect to a Windows share.

Regards,
Helgman

---

