---
title: "Postfix Not Resolving MX Records"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by mootpoint on 2008-05-19
This is a weird one, at least to me. I put a new machine up as an email server. It is receiving inbound email OK. However, when I send test email to my account at yahoo.com, it is stuck in the postfix queue. Here's what I get:

root@mercury:/etc/postfix# mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
93E3232A804F     1008 Mon May 19 00:25:17  [email]myaccount@mydomain.com[/email]
(Host or domain name not found. Name service error for name=yahoo.com type=MX: Host not found, try again)
                                         [email]myaccount@yahoo.com[/email]

But it's not a problem with my DNS server:

root@mercury:/etc/postfix# dig yahoo.com mx

; <<>> DiG 9.4.1-P1 <<>> yahoo.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31985
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 7, ADDITIONAL: 14

;; QUESTION SECTION:
;yahoo.com.                     IN      MX

;; ANSWER SECTION:
yahoo.com.              1208    IN      MX      1 d.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 e.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 f.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 g.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 a.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 b.mx.mail.yahoo.com.
yahoo.com.              1208    IN      MX      1 c.mx.mail.yahoo.com.

;; AUTHORITY SECTION:
yahoo.com.              166808  IN      NS      ns8.yahoo.com.
yahoo.com.              166808  IN      NS      ns1.yahoo.com.
yahoo.com.              166808  IN      NS      ns3.yahoo.com.
yahoo.com.              166808  IN      NS      ns2.yahoo.com.
yahoo.com.              166808  IN      NS      ns4.yahoo.com.
yahoo.com.              166808  IN      NS      ns6.yahoo.com.
yahoo.com.              166808  IN      NS      ns5.yahoo.com.

;; ADDITIONAL SECTION:
a.mx.mail.yahoo.com.    1621    IN      A       209.191.118.103
b.mx.mail.yahoo.com.    551     IN      A       66.196.97.250
c.mx.mail.yahoo.com.    1241    IN      A       216.39.53.3
c.mx.mail.yahoo.com.    1241    IN      A       216.39.53.2
d.mx.mail.yahoo.com.    246     IN      A       66.196.82.7
e.mx.mail.yahoo.com.    1621    IN      A       216.39.53.1
f.mx.mail.yahoo.com.    1286    IN      A       68.142.202.247
f.mx.mail.yahoo.com.    1286    IN      A       209.191.88.247
g.mx.mail.yahoo.com.    1620    IN      A       209.191.88.239
g.mx.mail.yahoo.com.    1620    IN      A       206.190.53.191
ns2.yahoo.com.          138182  IN      A       68.142.255.16
ns1.yahoo.com.          133888  IN      A       66.218.71.63
ns3.yahoo.com.          137749  IN      A       217.12.4.104
ns4.yahoo.com.          149065  IN      A       68.142.196.63

;; Query time: 74 msec
;; SERVER: 206.165.6.11#53(206.165.6.11)
;; WHEN: Mon May 19 00:38:56 2008
;; MSG SIZE  rcvd: 511


Can anyone help me understand why postfix can't resolve the yahoo.com mx record, but dig can? 

Help?

mootpoint

---

### Post by mootpoint on 2008-05-19
More information:

I can send mail between local accounts no problem. As far as I can tell, the only problem I need to solve is why the Postfix process doesn't get a good DNS result.

This is an Ubuntu box, recently upgraded, never in production for email until this weekend. The postfix install is chrooted, it appears, in /var/spool/postfix. Earlier in the process of bringing it online, I had to put static links in /var/spool/postfix/etc/resolv.conf and hosts to the "real" files in /etc. So I'm guessing my problem may have something to do with the chrooted postfix install? I temporarily gave the postfix user /bin/bash instead of /bin/false in /etc/passwd, and su'ed to the postfix account. It is able to get a good response to dig yahoo.com mx.

Here's my postconf output:

root@mercury:/home/dennis# postconf -n
alias_database = hash:/etc/postfix/maps/aliases
alias_maps = hash:/etc/postfix/maps/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 1h
header_checks = regexp:/etc/postfix/maps/header_checks
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
masquerade_domains = mydomain.com
mydestination = mercury.mydomain.com, localhost, localhost.localdomain
mydomain = mydomain.com
myhostname = mercury.mydomain.com
mynetworks = 127.0.0.0/8, 192.168.0.0/16
myorigin = mydomain.com
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_error_sleep_time = 60
smtpd_hard_error_limit = 10
smtpd_helo_restrictions = permit_mynetworks permit_sasl_authenticated reject_invalid_helo_hostname reject_non_fqdn_helo_hostname permit
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sender_restrictions = permit_mynetworks permit_sasl_authenticated reject_non_fqdn_sender reject_rhsbl_sender dsn.rfc-ignorant.org permit
smtpd_soft_error_limit = 60
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/mail/
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

Help? Anyone?

Dennis

---

