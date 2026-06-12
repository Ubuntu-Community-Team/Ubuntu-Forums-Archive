---
title: "postfix, unable to send/receive mail, forwarding to gmail"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Max1 on 2010-06-24
Hi,

I'm running Ubuntu 10.04 and I recently installed postfix following the guide at help.ubuntu.com/community/postfix.  I can not receive or send mail (sending mail through PHP and having mail sent to the server from gmail).  PHP registers the message as sent, but it never arrives in the target mailbox.  I've spent the past few hours browsing topics on google and nothing seems to be working for me.  My main.cf file looks like this (please note that I am also attempting to forward all incoming mail to my gmail account):

NOTE also that I replaced my domain name with example for this thread; I don't use example in my main.cf file.

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

content_filter = scan:127.0.0.1:10026
receive_override_options = no_address_mappings

readme_directory = no

#auth
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

#tls
smtp_use_tls = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
#smtp_tls_note_starttls_offer = yes # commented because used later in file
#tls_random_source = dev:/dev/urandom # commented because used later in file
smtp_tls_scert_verifydepth = 5
smtp_tls_key_file=/etc/postfix/certs/itchy.key
smtp_tls_cert_file=/etc/postfix/certs/itchy.pem
smtpd_tls_ask_ccert = yes
smtpd_tls_req_ccert =no
smtp_tls_enforce_peername = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = example.com, mail.example.com, localhost.example.com, localhost
relayhost = [smtp.gmail.com]:587
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,check_policy_service unix:private/policy-spf
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
spf-policyd_time_limit = 3600s

# DKIM
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891

```My mail log reads (/var/log/mail.log):

```

Jun 23 19:40:58 example-server1 postfix/master[24352]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 23 19:41:39 example-server1 postfix/master[24352]: terminating on signal 15
Jun 23 19:46:12 example-server1 postfix/master[24642]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 23 20:31:32 example-server1 postfix/master[24642]: terminating on signal 15
Jun 23 20:31:32 example-server1 postfix/master[24986]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 23 20:47:44 example-server1 postfix/smtpd[25428]: warning: ::1: address not listed for hostname localhost
Jun 23 20:47:44 example-server1 postfix/smtpd[25428]: connect from unknown[::1]
Jun 23 20:48:21 example-server1 postfix/smtpd[25428]: disconnect from unknown[::1]
Jun 23 20:51:41 example-server1 postfix/anvil[25431]: statistics: max connection rate 1/60s for (smtp:::1) at Jun 23 20:47:44
Jun 23 20:51:41 example-server1 postfix/anvil[25431]: statistics: max connection count 1 for (smtp:::1) at Jun 23 20:47:44
Jun 23 20:51:41 example-server1 postfix/anvil[25431]: statistics: max cache size 1 at Jun 23 20:47:44
Jun 23 20:54:00 example-server1 postfix/master[24986]: terminating on signal 15
Jun 23 20:54:00 example-server1 postfix/master[25541]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 23 21:25:51 example-server1 postfix/master[25541]: terminating on signal 15
Jun 23 21:25:51 example-server1 postfix/master[28382]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 23 21:38:07 example-server1 postfix/master[28382]: reload -- version 2.7.0, configuration /etc/postfix
Jun 23 21:49:56 example-server1 dkim-filter[31018]: Sendmail DKIM Filter v2.8.3 starting (args: -b v -x /etc/dkim-filter.conf -u dkim-filter -P /var/run/dkim-filter/dkim-filter.pid -p inet:8891@localhost)
Jun 23 22:02:48 example-server1 postfix/master[28382]: terminating on signal 15
Jun 23 22:02:48 example-server1 postfix/master[31244]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 24 00:54:42 example-server1 postfix/postmap[32118]: fatal: open database /etc/postfix/sasl_passwd.db: Permission denied
Jun 24 00:55:08 example-server1 postfix[32128]: error: to submit mail, use the Postfix sendmail command
Jun 24 00:55:08 example-server1 postfix[32128]: fatal: the postfix command is reserved for the superuser
Jun 24 00:55:23 example-server1 postfix/master[31244]: reload -- version 2.7.0, configuration /etc/postfix
Jun 24 01:11:44 example-server1 postfix/pickup[32151]: 9BB24BD617E: uid=33 from=<www-data>
Jun 24 01:11:44 example-server1 postfix/cleanup[32510]: 9BB24BD617E: message-id=<20100624051144.9BB24BD617E@mail.example.com>
Jun 24 01:11:45 example-server1 dkim-filter[31018]: 9BB24BD617E: no signature data
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 9BB24BD617E: from=<www-data@example.com>, size=405, nrcpt=1 (queue active)
Jun 24 01:11:45 example-server1 postfix/smtp[32513]: warning: cannot get RSA certificate from file /etc/postfix/certs/itchy.pem: disabling TLS support
Jun 24 01:11:45 example-server1 postfix/smtp[32513]: warning: TLS library problem: 32513:error:02001002:system library:fopen:No such file or directory:bss_file.c:356:fopen('/etc/postfix/certs/itchy.pem','r'):
Jun 24 01:11:45 example-server1 postfix/smtp[32513]: warning: TLS library problem: 32513:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:358:
Jun 24 01:11:45 example-server1 postfix/smtp[32513]: warning: TLS library problem: 32513:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:722:
Jun 24 01:11:45 example-server1 clamsmtpd: 100000: accepted connection from: 127.0.0.1
Jun 24 01:11:45 example-server1 postfix/smtpd[32516]: connect from localhost[127.0.0.1]
Jun 24 01:11:45 example-server1 postfix/smtpd[32516]: 37F04BD6180: client=localhost[127.0.0.1]
Jun 24 01:11:45 example-server1 postfix/cleanup[32510]: 37F04BD6180: message-id=<20100624051144.9BB24BD617E@mail.example.com>
Jun 24 01:11:45 example-server1 dkim-filter[31018]: 37F04BD6180: no signature data
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 37F04BD6180: from=<www-data@example.com>, size=632, nrcpt=1 (queue active)
Jun 24 01:11:45 example-server1 clamsmtpd: 100000: from=www-data@example.com, to=kazeseraph@gmail.com, status=CLEAN
Jun 24 01:11:45 example-server1 postfix/smtp[32513]: 9BB24BD617E: to=<kazeseraph@gmail.com>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.64, delays=0.52/0.02/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 37F04BD6180)
Jun 24 01:11:45 example-server1 postfix/smtpd[32516]: disconnect from localhost[127.0.0.1]
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 9BB24BD617E: removed
Jun 24 01:11:45 example-server1 postfix/smtp[32519]: warning: cannot get RSA certificate from file /etc/postfix/certs/itchy.pem: disabling TLS support
Jun 24 01:11:45 example-server1 postfix/smtp[32519]: warning: TLS library problem: 32519:error:02001002:system library:fopen:No such file or directory:bss_file.c:356:fopen('/etc/postfix/certs/itchy.pem','r'):
Jun 24 01:11:45 example-server1 postfix/smtp[32519]: warning: TLS library problem: 32519:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:358:
Jun 24 01:11:45 example-server1 postfix/smtp[32519]: warning: TLS library problem: 32519:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:722:
Jun 24 01:11:45 example-server1 postfix/smtp[32519]: 37F04BD6180: to=<kazeseraph@gmail.com>, relay=smtp.gmail.com[74.125.95.109]:587, delay=0.35, delays=0.04/0.01/0.25/0.05, dsn=5.7.0, status=bounced (host smtp.gmail.com[74.125.95.109] said: 530 5.7.0 Must issue a STARTTLS command first. u6sm39603803ibu.0 (in reply to MAIL FROM command))
Jun 24 01:11:45 example-server1 postfix/cleanup[32510]: 9C768BD6183: message-id=<20100624051145.9C768BD6183@mail.example.com>
Jun 24 01:11:45 example-server1 postfix/bounce[32520]: 37F04BD6180: sender non-delivery notification: 9C768BD6183
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 9C768BD6183: from=<>, size=2639, nrcpt=1 (queue active)
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 37F04BD6180: removed
Jun 24 01:11:45 example-server1 postfix/local[32521]: warning: maildir access problem for UID/GID=33/33: create maildir file /var/www/Maildir/tmp/1277356305.P32521.example-server1: Permission denied
Jun 24 01:11:45 example-server1 postfix/local[32521]: warning: perhaps you need to create the maildirs in advance
Jun 24 01:11:45 example-server1 postfix/local[32521]: 9C768BD6183: to=<www-data@example.com>, relay=local, delay=0.02, delays=0/0/0/0.01, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /var/www/Maildir/tmp/1277356305.P32521.example-server1: Permission denied)
Jun 24 01:11:45 example-server1 postfix/qmgr[32150]: 9C768BD6183: removed
Jun 24 01:36:00 example-server1 postfix/pickup[32151]: 7B1A6BD6183: uid=33 from=<www-data>
Jun 24 01:36:00 example-server1 postfix/cleanup[32693]: 7B1A6BD6183: message-id=<20100624053600.7B1A6BD6183@mail.example.com>
Jun 24 01:36:00 example-server1 dkim-filter[31018]: 7B1A6BD6183: no signature data
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: 7B1A6BD6183: from=<www-data@example.com>, size=405, nrcpt=1 (queue active)
Jun 24 01:36:00 example-server1 postfix/smtp[32695]: warning: cannot get RSA certificate from file /etc/postfix/certs/itchy.pem: disabling TLS support
Jun 24 01:36:00 example-server1 postfix/smtp[32695]: warning: TLS library problem: 32695:error:02001002:system library:fopen:No such file or directory:bss_file.c:356:fopen('/etc/postfix/certs/itchy.pem','r'):
Jun 24 01:36:00 example-server1 postfix/smtp[32695]: warning: TLS library problem: 32695:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:358:
Jun 24 01:36:00 example-server1 postfix/smtp[32695]: warning: TLS library problem: 32695:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:722:
Jun 24 01:36:00 example-server1 clamsmtpd: 100001: accepted connection from: 127.0.0.1
Jun 24 01:36:00 example-server1 postfix/smtpd[32697]: connect from localhost[127.0.0.1]
Jun 24 01:36:00 example-server1 postfix/smtpd[32697]: 8BD13BD6182: client=localhost[127.0.0.1]
Jun 24 01:36:00 example-server1 postfix/cleanup[32693]: 8BD13BD6182: message-id=<20100624053600.7B1A6BD6183@mail.example.com>
Jun 24 01:36:00 example-server1 dkim-filter[31018]: 8BD13BD6182: no signature data
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: 8BD13BD6182: from=<www-data@example.com>, size=632, nrcpt=1 (queue active)
Jun 24 01:36:00 example-server1 clamsmtpd: 100001: from=www-data@example.com, to=kazeseraph@gmail.com, status=CLEAN
Jun 24 01:36:00 example-server1 postfix/smtp[32695]: 7B1A6BD6183: to=<kazeseraph@gmail.com>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.12, delays=0.02/0.01/0.05/0.04, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 8BD13BD6182)
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: 7B1A6BD6183: removed
Jun 24 01:36:00 example-server1 postfix/smtpd[32697]: disconnect from localhost[127.0.0.1]
Jun 24 01:36:00 example-server1 postfix/smtp[32700]: warning: cannot get RSA certificate from file /etc/postfix/certs/itchy.pem: disabling TLS support
Jun 24 01:36:00 example-server1 postfix/smtp[32700]: warning: TLS library problem: 32700:error:02001002:system library:fopen:No such file or directory:bss_file.c:356:fopen('/etc/postfix/certs/itchy.pem','r'):
Jun 24 01:36:00 example-server1 postfix/smtp[32700]: warning: TLS library problem: 32700:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:358:
Jun 24 01:36:00 example-server1 postfix/smtp[32700]: warning: TLS library problem: 32700:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:722:
Jun 24 01:36:00 example-server1 postfix/smtp[32700]: 8BD13BD6182: to=<kazeseraph@gmail.com>, relay=smtp.gmail.com[74.125.95.109]:587, delay=0.27, delays=0.04/0.01/0.17/0.05, dsn=5.7.0, status=bounced (host smtp.gmail.com[74.125.95.109] said: 530 5.7.0 Must issue a STARTTLS command first. u6sm39701407ibu.6 (in reply to MAIL FROM command))
Jun 24 01:36:00 example-server1 postfix/cleanup[32693]: D9D29BD6184: message-id=<20100624053600.D9D29BD6184@mail.example.com>
Jun 24 01:36:00 example-server1 postfix/bounce[32701]: 8BD13BD6182: sender non-delivery notification: D9D29BD6184
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: D9D29BD6184: from=<>, size=2639, nrcpt=1 (queue active)
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: 8BD13BD6182: removed
Jun 24 01:36:00 example-server1 postfix/local[32702]: warning: maildir access problem for UID/GID=33/33: create maildir file /var/www/Maildir/tmp/1277357760.P32702.example-server1: Permission denied
Jun 24 01:36:00 example-server1 postfix/local[32702]: warning: perhaps you need to create the maildirs in advance
Jun 24 01:36:00 example-server1 postfix/local[32702]: D9D29BD6184: to=<www-data@example.com>, relay=local, delay=0.01, delays=0/0/0/0, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /var/www/Maildir/tmp/1277357760.P32702.example-server1: Permission denied)
Jun 24 01:36:00 example-server1 postfix/qmgr[32150]: D9D29BD6184: removed

```And my error log (/var/log/mail.err)

```

Jun 24 00:54:42 example-server1 postfix/postmap[32118]: fatal: open database /etc/postfix/sasl_passwd.db: Permission denied
Jun 24 00:55:08 example-server1 postfix[32128]: error: to submit mail, use the Postfix sendmail command
Jun 24 00:55:08 example-server1 postfix[32128]: fatal: the postfix command is reserved for the superuser
Jun 24 01:11:45 example-server1 dkim-filter[31018]: 9BB24BD617E: no signature data
Jun 24 01:11:45 example-server1 dkim-filter[31018]: 37F04BD6180: no signature data
Jun 24 01:36:00 example-server1 dkim-filter[31018]: 7B1A6BD6183: no signature data
Jun 24 01:36:00 example-server1 dkim-filter[31018]: 8BD13BD6182: no signature data

```Any suggestions?  Perhaps a point in the right direction, a step by step guide maybe?  Help in this matter is greatly appreciated.

Thanks

---

### Post by Max1 on 2010-06-24
Okay, so I got PHP to send mail again by removing all the suggestions I found on google which enable mail forwarding; namely by removing these lines:

```

#auth
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

#tls
smtp_use_tls = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
#smtp_tls_note_starttls_offer = yes # commented because used later in file
#tls_random_source = dev:/dev/urandom # commented because used later in file
smtp_tls_scert_verifydepth = 5
smtp_tls_key_file=/etc/postfix/certs/itchy.key
smtp_tls_cert_file=/etc/postfix/certs/itchy.pem
smtpd_tls_ask_ccert = yes
smtpd_tls_req_ccert =no
smtp_tls_enforce_peername = no

```and changing relayhost back to empty as was set up in the original installation.

```

relayhost =

```Half the problem solved; however, the issues only arose when I attempted to forward email to gmail.  This is still desired.  Can anyone point me to a suitable and reliable location which guides me through this process (forwarding mail to gmail from postfix)?

Also, the message was sent under the name www-data.  How do I change this?

Thanks

---

### Post by karthick87 on 2010-10-27
Me too have the same problem..Someone help..

---

