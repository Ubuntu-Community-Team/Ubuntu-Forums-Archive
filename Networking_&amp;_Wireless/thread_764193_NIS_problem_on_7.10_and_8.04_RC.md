---
title: "NIS problem on 7.10 and 8.04 RC"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by mleisher on 2008-04-23
NIS server: OpenBSD 3.8

NIS client: Ubuntu 7.10 and 8.04 RC desktop versions with /home mounted from an OpenBSD 3.9 machine at boot time. Automounter not used. nsswitch.conf has passwd and shadow set to compat. passwd, shadow and group have the +:::.... entries added.

Problem: command line NIS lookups on the client work fine (i.e. "ypmatch user passwd"). When logging in as a non-local user, I get Access Denied or Authentication failure, depending on whether I am running login or su.

Am I missing something simple? Are there irreconcilable password differences between OpenBSD and Ubuntu?

---

### Post by mleisher on 2008-04-25
A hint in another post led me to the answer.

1. Use synaptic to download and install libpam-unix2.
2. Edit /etc/pam.d/common-auth so the first line looks like:
   auth requisite pam_unix2 nullok
3. Edit /etc/pam.d/common-password so the first line looks like:
   auth requisite pam_unix2 nullok obscure md5

This will allow authentication of passwords for non-local users.

The typical NIS setup for the desktop distribution acting as a NIS client to another machine:
1. Install nis. You will be asked for the NIS domain name during configuration.
2. Install nfs-common and nfs-kernel-server (for automounting). Add the following line to /etc/nsswitch.conf:
   automounter nis
3. Install pam_unix2 (edit pam files as recommended above).
4. Add the following line at the end of /etc/passwd:
   +::::::
5. Add the following line at the end of /etc/group:
   +:::
6. Add the following line at the end of /etc/shadow:
   +::::::::

---

