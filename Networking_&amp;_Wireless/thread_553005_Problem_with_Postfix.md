---
title: "Problem with Postfix"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by morrison1976 on 2007-09-17
Hello, I am quite new to Ubuntu so my apologies if this is something very simple.

I have setup an Intrusion Detection server with Snort, Tripwire etc on it and this server is sendign its log information to a second server which is acting as a central logging server.  I know that this part is all workign correctly as I can see the logs being recieved on the log server.  I have setup Swatch to parse through the logfile and to use Postfix to send an email whenever an event occurs.  I recieve some messages no problem but I never seem to get the Snort report and the error I get in postfix is shown below:

Sep 17 06:25:42 loghost postfix/smtp[6461]: F3BCD1140D0: to=<SupportTeam@**********.co.uk>, orig_to=<root>, relay=xx.xx.xx.xx[xx.xx.xx.xx]:25, delay=4.2, del$
Sep 17 06:25:42 loghost postfix/qmgr[3933]: F3BCD1140D0: removed
Sep 17 06:29:52 10.172.1.200 postfix/smtpd[5151]: connect from localhost[127.0.0.1]
Sep 17 06:29:52 10.172.1.200 postfix/smtpd[5151]: 3999BEB4021: client=localhost[127.0.0.1]
Sep 17 06:29:56 10.172.1.200 postfix/cleanup[5154]: 3999BEB4021: message-id=<20070917052952.3999BEB4021@IDS1.xxxxxxxxxx.co.uk>
Sep 17 06:29:56 10.172.1.200 postfix/smtpd[5151]: warning: 3999BEB4021: queue file size limit exceeded
Sep 17 06:30:16 10.172.1.200 postfix/smtpd[5151]: disconnect from localhost[127.0.0.1]
Sep 17 05:30:16 10.172.1.200 postfix/postdrop[5156]: warning: uid=0: Illegal seek
Sep 17 06:30:16 10.172.1.200 postfix/sendmail[5155]: fatal: root(0): queue file write error

I know that the postfix is working because I get other reports, but I seem to get these failures regularly and I'm certainly not getting everything I would expect.

here is my postfix -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
mailbox_size_limit = 0
message_size_limit = 10540000
mydestination = loghost.xxxxxxxxx.co.uk, localhost.xxxxxxxxxx.co.uk, localhost
myhostname = loghost.xxxxxxxxxx.co.uk
mynetworks = 127.0.0.0/8, xx.xx.xx.xx/16
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 10.172.2.2
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache


Any ideas anyone?

---

### Post by JinxAu on 2007-09-17
No Postfix expert, but according to the log file:
> Sep 17 06:29:56 10.172.1.200 postfix/smtpd[5151]: warning: 3999BEB4021: queue file size limit exceeded

Might be to do with the queue size?

Cya round
Jinx

---

### Post by morrison1976 on 2007-09-17
Thanks JinxAu but that response was as helpfull as a chocolate teapot is usefull.  I relaise there must be a problem with the 'queue size', what I don't undertand is what 'queue' is it talking about and where do I configure it?

---

### Post by JinxAu on 2007-09-17
> **morrison1976 said:**
> Thanks JinxAu but that response was as helpfull as a chocolate teapot is usefull.  I relaise there must be a problem with the 'queue size', what I don't undertand is what 'queue' is it talking about and where do I configure it?

Tried this thing called Google?

From [Postfix]("http://www.postfix.org/resource.html"):
>  message_size_limit (default: 10240000 bytes)
    The maximal size of a Postfix queue file, including envelope information (sender, recipient, etc.). t

Hope you're not this much of tool to everyone who tries to help you.

Cya round
Jinx

---

