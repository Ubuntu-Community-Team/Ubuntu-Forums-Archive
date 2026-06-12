---
title: "thc-hydra installation/dependencies help"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by herot on 2008-08-14
I am trying to compile hydra 5.4 from source and install it.
I have gotten this far:
```
root@herot-desktop:/home/herot/Desktop/hydra-5.4-src# ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from http://0xbadc0de.be !

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
root@herot-desktop:/home/herot/Desktop/hydra-5.4-src#

```

I couldn't figure out which packages corresponded to SAP or SVN. Does anyone know? Has anyone successfully gotten hydra running on Hardy?

---

### Post by djurny on 2009-08-07
> **herot said:**
> I am trying to compile hydra 5.4 from source and install it.
I have gotten this far:
```
root@herot-desktop:/home/herot/Desktop/hydra-5.4-src# ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from http://0xbadc0de.be !

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
root@herot-desktop:/home/herot/Desktop/hydra-5.4-src#

```

I couldn't figure out which packages corresponded to SAP or SVN. Does anyone know? Has anyone successfully gotten hydra running on Hardy?
i think svn means subversion

---

