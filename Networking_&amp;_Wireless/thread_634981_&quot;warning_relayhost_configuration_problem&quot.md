---
title: "&quot;warning: relayhost configuration problem&quot;"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by t_ras on 2007-12-08
Hi,
I can't send mail, the log keeps showing "warning: relayhost configuration problem" for send mails.
I can't figure out whats wronge, the main.cf seems to be OK (AFAICS).

May be you can see something I don't and save me from this frustration:confused:

Main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = serversrv1.servers.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = servers.net, serversrv1, localhost.localdomain, localhost,mail.servers.net,serversrv1.servers.net
relayhost = localhost
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,
# check_recipient_access hash:/etc/postfix/local-host-names
smtpd_tls_auth_only = No
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names

```
+How can I tell postfix to log sent mails?

---

### Post by t_ras on 2007-12-08
OK, I removed the "relayhost" command, and now it si working OK.

---

### Post by rocky_karat on 2008-05-19
Hi,

I am also facing the same problem. I am using Zimbra Collaboration Suite which uses postfix for smtp. 

Thanks

---

