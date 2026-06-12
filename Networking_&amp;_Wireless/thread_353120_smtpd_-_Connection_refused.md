---
title: "smtpd - Connection refused"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by mmoller on 2007-02-04
I am trying to set up a smtp server on my home network.  Ubuntu 6.0.6 is acting as the masquerading firewall proxy gateway.

I've tried both sendmail and exim, but get the same problem with both. When I "telnet 127.0.0.1 25" from a shell on the machine running the smtpd, I can connect just fine, but when I try "telnet 192.168.0.1 25" from the same shell, or from another machine on the network I get "Connection refused" errors, and no /var/log file gives any indication why.

This continues even with the iptables firewall disabled.  I have http (Apache), ssh, smb and even vnc working just fine, but cannot for the life of me get through to smtpd.  Where is the layer refusing connection? Is it perhaps pam? Where can I start to look?

regards
Michael

---

### Post by mmoller on 2007-02-04
Here's the netstat entry for the smtpd that does not work:
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     8780/exim4

Compared to, say, the httpd and sshd, which does:
tcp6       0      0 :::80                   :::*                    LISTEN     24957/apache2       
tcp6       0      0 :::22                   :::*                    LISTEN     3376/sshd

Why the difference? Any thoughts? Anyone?

---

