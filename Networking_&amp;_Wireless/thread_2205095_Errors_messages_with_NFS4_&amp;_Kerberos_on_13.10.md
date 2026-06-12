---
title: "Errors messages with NFS4 &amp; Kerberos on 13.10"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by bdemsky on 2014-02-12
I'm setting up both a server and client on Ubuntu 13.10 with nfs4 and kerberos with sec=krb5p.  The nfs filesystem mounts and appears to work fine.  But on the server I see the following messages in /var/log/syslog on the server:

Feb 11 21:43:02 plrg rpc.svcgssd[1099]: ERROR: GSS-API: error in gss_free_lucid_sec_context(): GSS_S_NO_CONTEXT (No context has been established) - Unknown error
Feb 11 21:43:02 plrg rpc.svcgssd[1099]: WARN: failed to free lucid sec context
Feb 11 21:43:02 plrg kernel: [23001.277331] RPC: AUTH_GSS upcall timed out.
Feb 11 21:43:02 plrg kernel: [23001.277331] Please check user daemon is running.
Feb 11 21:43:20 plrg kernel: [23019.307981] RPC: AUTH_GSS upcall timed out.
Feb 11 21:43:20 plrg kernel: [23019.307981] Please check user daemon is running.

---

