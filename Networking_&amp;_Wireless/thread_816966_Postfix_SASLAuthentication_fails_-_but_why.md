---
title: "Postfix: SASLAuthentication fails - but why?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by jo.angel on 2008-06-03
Hello out there,

I have set up a postfix server (Ubuntu 7.10) and want to send emails via a relay host (mail.gmx.de). To send mails i use mailx (command line). 
I have done a /etc/postfix/sasl_password angelegt and did the database. But I semm to hav a problem with authentification. If I send a mail:

    > mail -s "testbetreff" [email]info@meinkumpel.de[/email] < tmp


what I get in /var/log/mail.log is:
    > relay=mail.gmx.net[213.165.64.21]:25, delay=5.5, delays=0.03/0.02/5.4/0, dsn=5.7.0, status=bounced (SASL authentication failed; server mail.gmx.net[213.165.64.21] said: 535 5.7.0 Incorrect username or password {mp039}
As I understand it, the mail is sent to the relay host, but thats it...
If I telnet to port25 what i get is:

    > telnet localhost 25
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.
    220 xxx.yyy ESMTP Postfix (Ubuntu)
    ehlo localhost
    250-xxx.yyy
    250-PIPELINING
    250-SIZE 10240000
    250-VRFY
    250-ETRN
    250-STARTTLS
    250-ENHANCEDSTATUSCODES
    250-8BITMIME
    250 DSN


Shouldn't I get as well summink like
    > 250-AUTH

Some more infos: libsasl2-2, libsasl2-modules, sasl2-bin are installeds, aliases should be done correctly, and I have tried with all kinds of restarts
Heres's my main.cf:
    > smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
    biff = no
    append_dot_mydomain = no
    # TLS parameters
    smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
    smtpd_use_tls=yes
    smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
    smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

    # SASL parameters
    smtp_sasl_auth_enable = yes
    smtp_sasl_security_options = noanonymous
    smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
    myhostname = xxx.yyy
    alias_maps = hash:/etc/aliases
    alias_database = hash:/etc/aliases
    mydestination = xxx, xxx.yyy, localhost.yyy, localhost
    relayhost = mail.gmx.net
    mynetworks = 127.0.0.0/8
    mailbox_size_limit = 0
    recipient_delimiter = +
    inet_interfaces = all
    inet_protocols = all
    sender_canonical_maps = hash:/etc/postfix/sender_canonical

And my /etc/default/saslauthd:
    > START=yes
    MECHANISMS="pam"
    MECH_OPTIONS=""
    THREADS=5
    OPTIONS="-c"

Thanks for looking at this problem. If you can solve it on top of that you are my hero of the day!

---

