---
title: "Squid + dansguardian logging issue"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Xcalibur99 on 2007-11-09
I have a working installation of squid and dansguardian on the same machine. However since dansguardian is forwarding the traffic to squid, the access.log only shows the local ip as source. I know x-forwarded-for option will enable squid to accept the client ip-address through dansguardian, but my version of squid complains about the the option in the config file:

parseConfigFile: line 2460 unrecognized: 'follow_x_forwarded_for allow localhost'
parseConfigFile: line 2471 unrecognized: 'acl_uses_indirect_client on'
parseConfigFile: line 2482 unrecognized: 'delay_pool_uses_indirect_client on'
 parseConfigFile: line 2493 unrecognized: 'log_uses_indirect_client on'

I installed both squid and dansguardian apt-get. I am running the following version of squid:

root@xxxxxxx:/etc/squid# squid -v
Squid Cache: Version 2.6.STABLE1
configure options: '--prefix=/usr' '--exec_prefix=/usr' '--bindir=/usr/sbin' '--sbindir=/usr/sbin' '--libexecdir=/usr/lib/squid' '--sysconfdir=/etc/squid' '--localstatedir=/var/spool/squid' '--datadir=/usr/share/squid' '--enable-async-io' '--with-pthreads' '--enable-storeio=ufs,aufs,diskd,null' '--enable-linux-netfilter' '--enable-linux-proxy' '--enable-arp-acl' '--enable-epoll' '--enable-removal-policies=lru,heap' '--enable-snmp' '--enable-delay-pools' '--enable-htcp' '--enable-cache-digests' '--enable-underscores' '--enable-referer-log' '--enable-useragent-log' '--enable-auth=basic,digest,ntlm' '--enable-carp' '--with-large-files' 'i386-debian-linux' 'build_alias=i386-debian-linux' 'host_alias=i386-debian-linux' 'target_alias=i386-debian-linux'

Compiling squid with --enable-follow-x-forwarded-for will enable this. Can this argument be specified via apt-get? Any other way of enabeling x-forwarded-for with squid already installed?

---

