---
title: "What is my mail doing"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Joe325 on 2010-02-09
Hi,

Is anyone able to tell me what may /var/log/mail.log is doing - it looks very strange to me

Feb 10 09:28:48 linbox postfix/smtp[32540]: 7F5A730F7F: to=<b13k1l@relay.skynet.be>, relay=none, delay=156033, delays=155997/0.31/36/0, dsn=4.4.1, status=deferred (connect to relay.skynet.be[195.238.5.128]:25: Connection timed out)
Feb 10 09:28:48 linbox postfix/smtp[32513]: 146D63105C: to=<b@nf.com>, relay=none, delay=156030, delays=155994/0.18/36/0, dsn=4.4.1, status=deferred (connect to mx1.nf.com[10.42.23.11]:25: Connection timed out)
Feb 10 09:28:49 linbox postfix/smtp[32541]: connect to mail01.zmlaw.com[63.243.10.74]:25: Connection timed out
Feb 10 09:28:49 linbox postfix/smtp[32541]: 753A43596B: to=<lgierbolini@zmlaw.com>, relay=none, delay=372334, delays=372297/0.32/36/0, dsn=4.4.1, status=deferred (connect to mail01.zmlaw.com[63.243.10.74]:25: Connection timed out)
Feb 10 09:28:49 linbox postfix/smtp[32539]: connect to [www.dci.co.ir](www.dci.co.ir)[217.218.165.150]:25: Connection timed out
Feb 10 09:28:49 linbox postfix/smtp[32539]: 758E5376C2: to=<Pirouz@www.dci.co.ir>, relay=none, delay=380426, delays=380390/0.3/36/0, dsn=4.4.1, status=deferred (connect to [www.dci.co.ir](www.dci.co.ir)[217.218.165.150]:25: Connection timed out)
Feb 10 09:28:49 linbox postfix/smtp[32544]: connect to news.orange.fr[193.252.117.183]:25: Connection timed out
Feb 10 09:28:50 linbox postfix/smtp[32544]: 76361309F8: to=<ba4acef3@news.orange.fr>, relay=none, delay=156031, delays=155994/0.33/37/0, dsn=4.4.1, status=deferred (connect to news.orange.fr[193.252.117.183]:25: Connection timed out)
Feb 10 09:28:51 linbox postfix/smtp[32501]: connect to nemesis.nunet.nova.edu[137.52.128.54]:25: Connection timed out
Feb 10 09:28:52 linbox postfix/smtp[32547]: connect to al-sahraa.com[66.246.235.42]:25: Connection timed out
Feb 10 09:28:52 linbox postfix/smtp[32547]: 23709374FE: to=<pr@al-sahraa.com>, relay=none, delay=380396, delays=380357/0.35/39/0, dsn=4.4.1, status=deferred (connect to al-sahraa.com[66.246.235.42]:25: Connection timed out)
Feb 10 09:28:53 linbox postfix/smtp[32499]: 5E5E72FCD8: to=<alyousfi4@htomaill.com>, relay=none, delay=158336, delays=158296/0.14/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=htomaill.com type=MX: Host not found, try again)
Feb 10 09:28:53 linbox postfix/smtp[32505]: A99E62FCB4: to=<Amorita@yahoo.mx>, relay=none, delay=158061, delays=158020/0.15/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=yahoo.mx type=MX: Host not found, try again)
Feb 10 09:28:53 linbox postfix/smtp[32543]: 724A333C4A: to=<farhang@dpir.com>, relay=none, delay=380428, delays=380388/0.33/40/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=dpir.com type=MX: Host not found, try again)
Feb 10 09:28:54 linbox postfix/smtp[32524]: 6EACC36FF4: to=<info@wrightarchery.qc.ca>, relay=none, delay=372846, delays=372805/0.23/41/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=wrightarchery.qc.ca type=MX: Host not found, try again)
Feb 10 09:28:56 linbox postfix/smtp[32081]: 4F0F3342A9: to=<jim@belcherbows.com>, relay=mx5.biz.mail.yahoo.com[68.142.224.244]:25, delay=374471, delays=374127/0.18/344/0, dsn=4.7.1, status=deferred (host mx5.biz.mail.yahoo.com[68.142.224.244] refused to talk to me: 421 4.7.1 [TS03] All messages from My will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html))
Feb 10 09:28:56 linbox postfix/smtp[32514]: 17D2837D34: to=<humberto@emmanuelchurch.org>, relay=none, delay=372856, delays=372813/0.19/43/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=emmanuelchurch.org type=MX: Host not found, try again)
Feb 10 09:28:59 linbox postfix/smtp[32508]: AC7B930604: to=<andre.bovy@tele2allin.be>, relay=none, delay=158048, delays=158001/0.16/46/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=tele2allin.be type=MX: Host not found, try again)
Feb 10 09:29:16 linbox postfix/smtp[32520]: connect to mail2-asn.minefi.gouv.fr[160.92.112.92]:25: Connection timed out
Feb 10 09:29:16 linbox postfix/smtp[32520]: 65580305C4: to=<andre-claude.lacoste@asn.minefi.gouv.fr>, relay=none, delay=158066, delays=158003/0.21/63/0, dsn=4.4.1, status=deferred (connect to mail2-asn.minefi.gouv.fr[160.92.112.92]:25: Connection timed out)
Feb 10 09:29:21 linbox postfix/smtp[32501]: connect to charon.nunet.nova.edu[137.52.128.22]:25: Connection timed out
Feb 10 09:29:21 linbox postfix/smtp[32501]: C6F9837D1A: to=<goldmanp@nsu.law.nova.edu>, relay=none, delay=373003, delays=372934/0.14/68/0, dsn=4.4.1, status=deferred (connect to charon.nunet.nova.edu[137.52.128.22]:25: Connection timed out)
Feb 10 09:29:32 linbox imapd: Connection, ip=[::ffff:192.168.1.77]


These domains I have never heard of
Any ideas??

Thanks

---

### Post by lisati on 2010-02-09
Has a spambot managed to get hold of your server's address somehow and managed to connect and clutter up your mail queue?

Edit: Link to info on restricting access to your server: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by Joe325 on 2010-02-09
That article went on & on - I have changed my main.cf to below. Is there anything that looks out of place


myhostname = myFQDN
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com.au, linbox.mydomain.com.au, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.1/32 192.168.1.1/32
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

---

