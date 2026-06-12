---
title: "OPENSWAN versions (gutsy)"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by djm-uk on 2008-03-02
I am trying to connect via IPSEC to a sonicwall.  The Ubu machine is behind a router so I need NAT-T enabled. It is enabled in ipsec.conf (nat-traversal=yes) and on the Sonicwall but (once I turn the debug on!) I get a message about unrecognised IKE next header NAT-D (sic - not NAT-T).

It seems that the openswan client is not recognising the NAT Traversal option.  Looking at the openswan web site the current version is 2.5.15 but the version in the package manager is 2.4.6 and there are lots of bugfixes to do with NAT in the versions >2.4.6...

When I look in package manager I am confused as there is the Openswan package plus a 'kernel' patch package plus a 'source' package.  The openswan package seems to imply that I shouldn't need anything else..

I am a bit of a noob with linux - do I need to install the kernel 'patch' packages in package manager or how can I install the later version of openswan, do I just download from the openswan site and 'make' them ??  I don't really want to stuff my kernel *just* yet...

Thanks

David

---

