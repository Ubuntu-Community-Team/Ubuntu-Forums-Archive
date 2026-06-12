---
title: "ebox&amp;squid web cache proxy"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by salvor_hardin on 2009-06-08
I installed squid and ebox. When try to access ebox from [https://localhost/ebox](https://localhost/ebox) i get following message:

> localhost:443 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for <a id="cert_domain_link" title="eBox's Server">(null)</a>

(Error code: sec_error_untrusted_issuer)

During installation i get this message:

> "Warning: The home dir /var/lib/ebox/ you specified already exists.
Adding system user `ebox' (UID 115) ...
Adding new user `ebox' (UID 115) with group `ebox' ...
The home directory `/var/lib/ebox/' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/ebox/' does not belong to the user you are currently creating.
Adding user `ebox' to group `adm' ...
Adding user ebox to group adm
Done.
Creating the eboxlogs database
WARNING **: Owner of /tmp/orbit-hpg is not the current user
 * Restarting eBox module: apache   "

Apache is ok and running! I also installed squid to use web cache server for hotspot wireless system. I use AirLive MW2000S gateway. I configured squid following some instructions i found but still i get litle confused. I tried it and I think it is working but still when I check it i get message like:

>  * Restarting Squid HTTP Proxy 3.0 squid3                                                         *  Waiting...                                                                                    * ...                                                                                            * ...                                                                                            * ...                                                                                            * ...                                                                                            * ...                                                                                            * ...                                                                                            * ...                                                                                    [ OK ] 
2009/06/08 11:30:57| aclParseIpData: WARNING: Netmask masks away part of the specified IP in '192.168.2.1/16'
2009/06/08 11:30:57| cache_cf.cc(346) squid.conf:833 unrecognized: '			vhost'
                                                                                          [ OK ]

We have wireless system that can handle 120 users, satelite 2mbit internet connection, so you understand why I want squid operational...Any help would be appreciated!

Thanks!

---

### Post by salvor_hardin on 2009-06-08
I'm running latest 64 Ubuntu...9.04 Jaunty...

---

### Post by poundjd on 2009-06-08
I would suggest that you go to the eBox forum at [www.ebox-platform.com](www.ebox-platform.com) and post your questions, your much more likely to get good technical answers from the developers who are very active on the site.  Also, eBox has a squid module so your installation may have been compromised by the earlier installation of Squid.
-jeff

---

