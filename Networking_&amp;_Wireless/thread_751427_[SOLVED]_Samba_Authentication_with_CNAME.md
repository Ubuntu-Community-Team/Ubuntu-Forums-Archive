---
title: "[SOLVED] Samba Authentication with CNAME"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by BadServo on 2008-04-10
I've recently updated my aging Fedora File Server to rub Ubuntu Gutsy server.

The OS is installed, and samba is setup and running correctly, however I'm encountering an odd issue.  The server's hostname is "muggleton", but I've set up a CNAME in DNS to direct "files.mydomain.com" to "muggleton.mydomain.com".

This has always worked flawlessly in the past, but now, Windows Users cannot seem to authenticate when using the alias, onyl when using the actual hostname.

Any advice is certainly appreciated.

---

### Post by Eiríkr on 2008-04-10
A number of things changed in the move from the old smbfs type to the new cifs type.  It's possible your Fedora server was using the old smbfs internals; I'm not sure, by any means, but that might be what's going on.  

Instead of the CNAME in your DNS setup, or perhaps in addition to it, try using the **netbios aliases** option in the [global] section of your smb.conf file.  From [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NETBIOSALIASES"):
> This is a list of NetBIOS names that nmbd will advertise as additional names by which the Samba server is known. This allows one machine to appear in browse lists under multiple names. If a machine is acting as a browse server or logon server none of these names will be advertised as either browse server or logon servers, only the primary name of the machine will be advertised with these capabilities.

    Default: [font=courier]*netbios aliases = # empty string (no additional names)*[/font] 

    Example: [font=courier]*netbios aliases = TEST TEST1 TEST2*[/font]

So in your case, you'd add the following line to your [global] section:
```
netbios aliases = files
```
This way Samba will only share under \\files.  To share under \\muggleton as well, just add "muggleton" to the same line.  

HTH,

Eiríkr

---

### Post by BadServo on 2008-04-10
This initial tests I can run at the moment all appear successful.  This seems to have fixed things up nicely.

Thanks so much, mate.  I really appreciate the time and help.

---

### Post by Eiríkr on 2008-04-10
Glad it worked!  :)  Good luck with Hardy.  :D

Cheers,

Eiríkr

---

### Post by BadServo on 2008-04-12
It seems I spoke too soon.  I was in the office in person today (I do alot of support remotely) and found that the problem still persists.  Any other ideas are appreciated.

---

### Post by BadServo on 2008-04-14
A combination of configuration differences caused my continued issues.  The underlying problem of the alias not authenticating was, in fact, corrected by the above posted solution.  Thanks again.

---

