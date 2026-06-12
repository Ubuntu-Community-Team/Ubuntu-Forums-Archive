---
title: "Postfix and domain name"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by podianu on 2009-06-15
I use Ubuntu hardy and have installed postfix with dovecot with mutt. It is a stand alone PC directly connected to the internet and a few users. I would like to use postfix a a mailserver. Some outputs that are relevant. I am unsure of the various parameters to be filled in for the 

cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 podi
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Present configuration
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
append_dot_mydomain = no
mydomain = domain.tld
myhostname = mail.domain.tld
myorigin = $myhostname
mydestination = $myhostname
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = local.domain,localhost.localdomain,localhost
relayhost =
mynetworks = 127.0.0.0/127.0.1.8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
net_interfaces = all
html_directory = /usr/share/doc/postfix/html
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

Host specific information has confused me.
Do I need a FQDN?
As I understand one has to rely on the ISP, our ISP BSNL does not provide one to Home users.
Are the default settings OK.
I refer to the lines
mydomain = domain.tld
myhostname = mail.domain.tld
myorigin = $myhostname
mydestination = $myhostname

At present I am able to send mail from one of my users to me(root) and not on the net. In fact I am not able to send any mail to any user from me root.
Thanks

---

