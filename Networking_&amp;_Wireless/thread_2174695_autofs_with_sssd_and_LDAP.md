---
title: "autofs with sssd and LDAP"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by steve-ss on 2013-09-15
Hi
13.04
autofs is broken:
 [https://bugs.launchpad.net/linuxmint/+bug/1081489](https://bugs.launchpad.net/linuxmint/+bug/1081489)

I'm trying to build autofs with support for sssd. I downloaded and patched the source as per the above bug report. ./configure completes without error but the make bombs out:
 
> It won't build with or without antofs and autofs-ldap. sudo make fails
> with:
>
> lookup_ldap.c: En la función ‘lookup_init’:
> lookup_ldap.c:1487:2: aviso: declaración implícita de la función
> ‘parse_ldap_config’ [-Wimplicit-function-declaration]
> make[1]: *** [lookup_ldap.so] Error 1
> make[1]: se sale del directorio
> «/home/steve/Descargas/autofs-5.0.7/modules»
> make: *** [daemon] Error 2

I've tried with and without the broken autofs and autofs-ldap, but the error is the same.

Has anyone got autofs to talk to sssd?
Thanks,
Steve

---

### Post by steve-ss on 2013-09-17
OK, found it. Need to patch autofs:
[http://lists.wpkg.org/pipermail/autofs/2013-July/000152.html](http://lists.wpkg.org/pipermail/autofs/2013-July/000152.html)
HTH

---

