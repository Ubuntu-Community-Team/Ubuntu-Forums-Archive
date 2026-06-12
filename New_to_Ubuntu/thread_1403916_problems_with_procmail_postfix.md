---
title: "problems with procmail/ postfix"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Joe325 on 2010-02-10
Hi,

I have setup my own ubuntu 910 server from home which hosts my website and run my own mail. All was working well until I tries to install spamassassin. I then tried to remove spamassassin and my mail will no longer receive - even locally.
my mail.log error shows the following:

Feb 11 12:02:28 linbox postfix/cleanup[5841]: CBE742C909: message-id=<e5d519f2a81aa9df62173aa0b326e21d@linbox.domain.com.au>
Feb 11 12:02:28 linbox imapd: LOGOUT, user=me, ip=[::ffff:192.168.1.77], headers=0, body=0, rcvd=1197, sent=132, time=0
Feb 11 12:02:28 linbox postfix/qmgr[5805]: CBE742C909: from=<me@domain.com.au>, size=1272, nrcpt=1 (queue active)
Feb 11 12:02:29 linbox postfix/local[5845]: CBE742C909: to=<me@domain.com.au>, relay=local, delay=0.31, delays=0.3/0.01/0/0, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

The file /usr/bin/procmail exists but there is nothing in it.
My main.cf looks like this:


myhostname = linbox.domain.com.au
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain.com.au, localhost.domain.com.au, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 192.168.1.0/24
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

Can anyone explain to me what should be in the procmail & procmailrc files or where Im going wrong


Anyone know what Ive done

Thanks

---

### Post by Joe325 on 2010-02-11
I have managed to solve this

Seems I had a file in my home directory (.forwards)which was forwarding mail to the error shown above /usr/bin......

File was removed, reconfigured postfix - All Solved :p

---

