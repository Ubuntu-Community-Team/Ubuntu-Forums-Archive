---
title: "Microsoft LDAP signing &amp; Ubuntu"
date: 2023-02-09
forum: Networking &amp; Wireless
---

### Post by ferriswheel50 on 2023-02-09
I'm having issues getting my Ubuntu server to interface with a Windows AD server which has LDAP signing enabled. My Ubuntu server runs a webapp which uses LDAP to authenticate users. However, we just enabled LDAP signing on the MS AD server, and that broke the webapp authentication. 

Does Ubuntu support this feature? If so, how would I go about enabling/configuring it?

---

### Post by TheFu on 2023-02-10
> **ferriswheel50 said:**
> I'm having issues getting my Ubuntu server to interface with a Windows AD server which has LDAP signing enabled. My Ubuntu server runs a webapp which uses LDAP to authenticate users. However, we just enabled LDAP signing on the MS AD server, and that broke the webapp authentication. 

Does Ubuntu support this feature? If so, how would I go about enabling/configuring it?

When I was connecting webapps to an LDAP server, it was the application that managed it, not the OS.  The question that needs to be asked is whether the webapp is configured to support LDAP.  

MS-AD is a little different from a standard LDAP, but usually close enough to work like any other Unix-based LDAP for authentication.
A quick websearch seems to only return "LDAP signing" as a MSFT thing.  Did they, once again, embrace and extend, without following the RFC process? [https://ldap.com/ldap-related-rfcs/](https://ldap.com/ldap-related-rfcs/)  Hopefully, not. Perhaps the MSFT terminology is just different from what the rest of the world calls it?  MSFT, Apple, commonly do stuff like that.

---

