---
title: "SVN Checkout errors"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by pixar on 2009-11-18
Hi,

I have been using svn for a long time, it works for all other repos, but one specific one I get errors regarding ssl. 

svn: PROPFIND request failed on '/svn/gnunet'
svn: PROPFIND of '/svn/gnunet': SSL negotiation failed: SSL disabled due to library version mismatch ([https://gnunet.org](https://gnunet.org))

Any ideas what maybe wrong??

Thanks.

---

### Post by pixar on 2009-11-18
Hi,

This is sort of urgent, I can check out other repos with no problem. What should I do, what do you think the problem is?

---

### Post by sandyd on 2009-11-18
> **pixar said:**
> Hi,

This is sort of urgent, I can check out other repos with no problem. What should I do, what do you think the problem is?
try downgrading subversion or upgrading openssl.

---

### Post by pixar on 2009-11-18
tried both, infact built openssl newest version, same problem. I got someone else to try it from their system and it works :(

---

### Post by andrew.46 on 2009-11-19
Hi pixar,

> **pixar said:**
> I got someone else to try it from their system and it works :(

As it does on mine:


```
andrew@skamandros~/Desktop$ **[COLOR="Red"]svn checkout https://gnunet.org/svn/GNUnet/[/COLOR]**
Error validating server certificate for 'https://gnunet.org:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: gnunet.org
 - Valid: from Tue, 04 Jan 2005 16:54:40 GMT until Fri, 21 May 2032 16:54:40 GMT
 - Issuer: gnunet.org, Los Angeles, California, US
 - Fingerprint: 76:0b:c7:48:ca:a7:75:54:8e:f7:bc:ff:8e:6a:cb:b0:42:ae:42:fd
(R)eject, accept (t)emporarily or accept (p)ermanently? t
A    GNUnet/m4
A    GNUnet/m4/lib-link.m4
A    GNUnet/m4/printf-posix.m4
```

But what is the *exact* command you are using?

Andrew

---

### Post by pixar on 2009-11-19
@andrew.46

The same as you are: svn checkout [https://gnunet.org/svn/GNUnet/](https://gnunet.org/svn/GNUnet/)

---

