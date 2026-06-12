---
title: "squid and squidGuard not working"
date: 2024-04-24
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2024-04-24
squid with support for SSL Bumping
sudo apt install squid-openssl squidguard 

When i do squid without the squidguard every thing works but the content filtering. When I add url_rewrite_program /usr/bin/squidGuard to the /etc/squid/squid.conf to enable squidguard I get not internet. I have attached my /etc/squid/squid.conf in a zip file at the end.

```

$ squid -v
Squid Cache: Version 6.1
Service Name: squid
Ubuntu linux

This binary uses OpenSSL 3.0.10 1 Aug 2023. configure options:  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--disable-option-checking' '--disable-silent-rules' '--libdir=${prefix}/lib/x86_64-linux-gnu' '--runstatedir=/run' '--disable-maintainer-mode' '--disable-dependency-tracking' 'BUILDCXXFLAGS=-g -O2 -ffile-prefix-map=/build/squid-n48wD1/squid-6.1=. -flto=auto -ffat-lto-objects -fstack-protector-strong -fstack-clash-protection -Wformat -Werror=format-security -fcf-protection -fdebug-prefix-map=/build/squid-n48wD1/squid-6.1=/usr/src/squid-6.1-2ubuntu1.3 -Wno-error=deprecated-declarations -Wdate-time -D_FORTIFY_SOURCE=2 -Wl,-Bsymbolic-functions -flto=auto -ffat-lto-objects -Wl,-z,relro -Wl,-z,now ' 'BUILDCXX=g++' '--with-build-environment=default' '--enable-build-info=Ubuntu linux' '--datadir=/usr/share/squid' '--sysconfdir=/etc/squid' '--libexecdir=/usr/lib/squid' '--mandir=/usr/share/man' '--enable-inline' '--disable-arch-native' '--enable-async-io=8' '--enable-storeio=ufs,aufs,diskd,rock' '--enable-removal-policies=lru,heap' '--enable-delay-pools' '--enable-cache-digests' '--enable-icap-client' '--enable-follow-x-forwarded-for' '--enable-auth-basic=DB,fake,getpwnam,LDAP,NCSA,PAM,POP3,RADIUS,SASL,SMB' '--enable-auth-digest=file,LDAP' '--enable-auth-negotiate=kerberos,wrapper' '--enable-auth-ntlm=fake,SMB_LM' '--enable-external-acl-helpers=file_userip,kerberos_ldap_group,LDAP_group,session,SQL_session,time_quota,unix_group,wbinfo_group' '--enable-security-cert-validators=fake' '--enable-storeid-rewrite-helpers=file' '--enable-url-rewrite-helpers=fake' '--enable-eui' '--enable-esi' '--enable-icmp' '--enable-zph-qos' '--enable-ecap' '--disable-translation' '--with-swapdir=/var/spool/squid' '--with-logdir=/var/log/squid' '--with-pidfile=/run/squid.pid' '--with-filedescriptors=65536' '--with-large-files' '--with-default-user=proxy' '--enable-linux-netfilter' '--with-systemd' '--with-openssl' '--enable-ssl-crtd' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2 -ffile-prefix-map=/build/squid-n48wD1/squid-6.1=. -flto=auto -ffat-lto-objects -fstack-protector-strong -fstack-clash-protection -Wformat -Werror=format-security -fcf-protection -fdebug-prefix-map=/build/squid-n48wD1/squid-6.1=/usr/src/squid-6.1-2ubuntu1.3 -Wno-error=deprecated-declarations' 'LDFLAGS=-Wl,-Bsymbolic-functions -flto=auto -ffat-lto-objects -Wl,-z,relro -Wl,-z,now ' 'CPPFLAGS=-Wdate-time -D_FORTIFY_SOURCE=2' 'CXXFLAGS=-g -O2 -ffile-prefix-map=/build/squid-n48wD1/squid-6.1=. -flto=auto -ffat-lto-objects -fstack-protector-strong -fstack-clash-protection -Wformat -Werror=format-security -fcf-protection -fdebug-prefix-map=/build/squid-n48wD1/squid-6.1=/usr/src/squid-6.1-2ubuntu1.3 -Wno-error=deprecated-declarations'

```

vim /etc/squidguard/squidGuard.conf
```

dbhome /var/lib/squidguard/db
logdir /var/log/squidguard

dest adult {
        domainlist      adult/domains
        urllist         adult/urls
        expressionlist  adult/expressions
        redirect https://www.msn.com
}

acl {
    default {
        pass !adult all
        redirect https://www.google.com
    }
}

```

No squidGuard enabled
sudo systemctl status squid
```

&#9679; squid.service - Squid Web Proxy Server
     Loaded: loaded (/lib/systemd/system/squid.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-04-24 15:05:32 MDT; 34min ago
       Docs: man:squid(8)
    Process: 74422 ExecStartPre=/usr/sbin/squid --foreground -z (code=exited, status=0/SUCCESS)
   Main PID: 74426 (squid)
      Tasks: 9 (limit: 5710)
     Memory: 39.4M
        CPU: 19.076s
     CGroup: /system.slice/squid.service
             &#9500;&#9472;74426 /usr/sbin/squid --foreground -sYC
             &#9500;&#9472;74428 "(squid-1)" --kid squid-1 --foreground -sYC
             &#9500;&#9472;74429 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;74430 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;74431 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;74432 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;74433 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;74434 "(logfile-daemon)" /var/log/squid/access.log
             &#9492;&#9472;74435 "(pinger)"

Apr 24 15:05:32 plexmediaserver squid[74428]: Set Current Directory to /var/spool/squid
Apr 24 15:05:32 plexmediaserver squid[74428]: Finished loading MIME types and icons.
Apr 24 15:05:32 plexmediaserver squid[74428]: HTCP Disabled.
Apr 24 15:05:32 plexmediaserver squid[74428]: Pinger socket opened on FD 25
Apr 24 15:05:32 plexmediaserver squid[74428]: Squid plugin modules loaded: 0
Apr 24 15:05:32 plexmediaserver squid[74428]: Adaptation support is off.
Apr 24 15:05:32 plexmediaserver squid[74428]: Accepting SSL bumped HTTP Socket connections at conn13 local=[::]:3128 remote=[::] FD 23 flags=9
                                                  listening port: 3128
Apr 24 15:05:32 plexmediaserver systemd[1]: Started squid.service - Squid Web Proxy Server.
Apr 24 15:05:33 plexmediaserver squid[74428]: storeLateRelease: released 0 objects
Apr 24 15:20:15 plexmediaserver squid[74428]: parse URL too large (9311 bytes)
                                                  current from-client connection: conn2106 local=192.168.2.9:3128 remote=192.168.3.12:53593 FD 16 flags=1


```

WITH squidGuard enabled
sudo systemctl status squid
```

&#9679; squid.service - Squid Web Proxy Server
     Loaded: loaded (/lib/systemd/system/squid.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-04-24 15:54:00 MDT; 1min 13s ago
       Docs: man:squid(8)
    Process: 75032 ExecStartPre=/usr/sbin/squid --foreground -z (code=exited, status=0/SUCCESS)
   Main PID: 75037 (squid)
      Tasks: 18 (limit: 5710)
     Memory: 340.8M
        CPU: 3min 57.018s
     CGroup: /system.slice/squid.service
             &#9500;&#9472;75037 /usr/sbin/squid --foreground -sYC
             &#9500;&#9472;75039 "(squid-1)" --kid squid-1 --foreground -sYC
             &#9500;&#9472;75040 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;75041 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;75042 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;75043 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;75044 "(security_file_certgen)" -s /var/lib/squid/ssl_db -M 4MB
             &#9500;&#9472;75045 "(logfile-daemon)" /var/log/squid/access.log
             &#9500;&#9472;75046 "(pinger)"
             &#9500;&#9472;75047 "(squidGuard)"
             &#9500;&#9472;75048 "(squidGuard)"
             &#9500;&#9472;75050 "(squidGuard)"
             &#9500;&#9472;75054 "(squidGuard)"
             &#9500;&#9472;75060 "(squidGuard)"
             &#9500;&#9472;75061 "(squidGuard)"
             &#9500;&#9472;75062 "(squidGuard)"
             &#9500;&#9472;75064 "(squidGuard)"
             &#9492;&#9472;75073 "(squidGuard)"

Apr 24 15:54:45 plexmediaserver squid[75039]: Starting new redirector helpers...
                                                  current master transaction: master67
Apr 24 15:54:45 plexmediaserver squid[75039]: helperOpenServers: Starting 1/20 'squidGuard' processes
                                                  current master transaction: master67
Apr 24 15:54:45 plexmediaserver squid[75039]: Starting new redirector helpers...
                                                  current master transaction: master69
Apr 24 15:54:45 plexmediaserver squid[75039]: helperOpenServers: Starting 1/20 'squidGuard' processes
                                                  current master transaction: master69
Apr 24 15:54:47 plexmediaserver squid[75039]: Starting new redirector helpers...
                                                  current master transaction: master71
Apr 24 15:54:47 plexmediaserver squid[75039]: helperOpenServers: Starting 1/20 'squidGuard' processes
                                                  current master transaction: master71
Apr 24 15:54:49 plexmediaserver squid[75039]: Starting new redirector helpers...
                                                  current master transaction: master73
Apr 24 15:54:49 plexmediaserver squid[75039]: helperOpenServers: Starting 1/20 'squidGuard' processes
                                                  current master transaction: master73
Apr 24 15:55:09 plexmediaserver squid[75039]: Starting new redirector helpers...
                                                  current master transaction: master78
Apr 24 15:55:09 plexmediaserver squid[75039]: helperOpenServers: Starting 1/20 'squidGuard' processes
                                                  current master transaction: master78


```

[ATTACH]293690[/ATTACH]

---

