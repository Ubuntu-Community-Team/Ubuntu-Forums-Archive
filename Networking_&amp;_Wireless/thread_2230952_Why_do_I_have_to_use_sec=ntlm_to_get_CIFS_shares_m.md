---
title: "Why do I have to use sec=ntlm to get CIFS shares mounted?"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by rvdmeijden+launchpad on 2014-06-22
Hi,

Just a quick question. For years mounting CIFS shares via fstab or mount has worked well for me but it seems to have changed a bit. I now have to add [COLOR=#000000][FONT=Cantarell]sec=ntlm to het mounting options to get is to mount. Otherwise I get a error 95.

Why do I need this option "[COLOR=#000000][FONT=Cantarell]sec=ntlm" and what does it do?

I'd like to understand the change.

I hope someone has a clear answer.

Thanks
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Morbius1 on 2014-06-22
"sec" is the security mode and determines how passwords are encrypted between server and client ( even if you don't require passwords ).

ntlm used to be the default which is why you never had to specify it discretely. Things have moved on however so the default is now ntlmssp. If you are accessing something which doesn't speak ntlmssp you have to override the new default with the old one.

Most NAS devices use older technology so they often require ntlm. If you access an OSX samba share however it requires ntlmssp so before you had to specify that in the mount options but now you don't.

There are winners and losers with every change.

If you run the following command you will see the whole range of sec modes available:
```
 man mount.cifs
```

---

