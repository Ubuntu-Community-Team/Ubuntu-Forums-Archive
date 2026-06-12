---
title: "Postfix Installation Failure"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by lwoodtri on 2006-11-03
Good Morning / Afternoon All,

I am trying to install AIDE, and when it attempts to the postfix dependency, it fails with the error below.  I looked at the error and started back tracking from the prompts on the screen, and it looks like some sort of LDAP probelm in adding the postfix group.  Has anybody seen this before, or know how to resolve.  I am rather new to apt and ubuntu, so I am not exacltly sure of the interworkings . . . yet.  Anyway any pointers or direction would be greatly appreciated! 

Error: (see high-lighted)
=============================================================
root@test3:/var/lib/dpkg/info# apt-get install postfix
Reading package lists... Done
Building dependency tree... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.10-1ubuntu0.1) ...
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   :[B][COLOR="Red"] /build/buildd/openldap2-2.1.30/libraries/liblber/sockbuf.c:82: ber_sockbuf_ctrl: Assertion `( (sb)->sb_opts.lbo_valid == 0x3 )' failed.
/var/lib/dpkg/info/postfix.postinst: line 199: 18244 Aborted                 addgroup --system postfix[/COLOR][/B]
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 134
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aide:
 aide depends on mailx; however:
  Package mailx is not configured yet.
dpkg: error processing aide (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 aide
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

