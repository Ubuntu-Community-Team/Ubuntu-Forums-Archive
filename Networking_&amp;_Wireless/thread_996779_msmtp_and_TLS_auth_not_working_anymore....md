---
title: "msmtp and TLS auth not working anymore..."
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by asbesto on 2008-11-29
Hi, I have this very strange problem, so here is another message that I'm sure I will not have any answer at all... :( 

[B]Edit: so I found the answer by myself - AND IT WASN'T FUNNY.
[/B]

I had a TLS problem with mutt and msmtp. Here it is:

> 
msmtp: TLS certificate verification failed: the certificate is not trusted
msmtp: could not send mail (account default from /home/asbesto/.msmtprc)


Obviously, I have all certs, as I have them from some days, and I had no problem in these days. they are not changed, the md5sums for them are correct.

Manually launching msmtp for debugging give me this:

> 

[email]asbesto@gemini:~/.ssl[/email]/certs$ msmtp -d --serverinfo --host=mail.xxx.org --tls=on --tls-certcheck=on --tls-trust-file=./xxxmsmtp.pem 
host            = mail.xxx.org
port            = 25
timeout         = off
protocol        = smtp
domain          = localhost
auth            = none
user            = (not set)
password        = (not set)
ntlmdomain      = (not set)
tls             = on
tls_starttls    = on
tls_trust_file  = ./xxxmsmtp.pem
tls_key_file    = (not set)
tls_cert_file   = (not set)
tls_certcheck   = on
tls_force_sslv3 = off
<-- 220 xxx.org ESMTP Postfix (Debian/GNU)
--> EHLO localhost
<-- 250-xxx.org
<-- 250-PIPELINING
<-- 250-SIZE 10240000
<-- 250-VRFY
<-- 250-ETRN
<-- 250-STARTTLS
<-- 250-ENHANCEDSTATUSCODES
<-- 250-8BITMIME
<-- 250 DSN
--> STARTTLS
<-- 220 2.0.0 Ready to start TLS
msmtp: TLS certificate verification failed: the certificate is not trusted
[email]asbesto@gemini:~/.ssl[/email]/certs$ 



my msmtprc:

> 

asbesto@gemini:~$ cat .msmtprc
account default
host mail.xxx.org
port 25
from [email]asbesto@xxx.org[/email]
auth on
user [email]asbesto@xxx.org[/email]
password eatmyshorts
tls on
tls_certcheck on
tls_starttls on
tls_trust_file /home/asbesto/.ssl/certs/xxxmsmtp.pem
logfile ~/.msmtp_log
asbesto@gemini:~$ 




and in my muttrc I have these lines:

> 

set certificate_file="/home/asbesto/.ssl/certs/ca-freaknetdyne.cer"
set sendmail ="/usr/bin/msmtp -d"  



the -d is for debugging, and it gave me this output when sending mail from mutt:

> 

msmtp: TLS certificate verification failed: the certificate is not trusted
msmtp: could not send mail (account default from /home/asbesto/.msmtprc)
ignoring system configuration file /etc/msmtprc: No such file or directory
loaded user configuration file /home/asbesto/.msmtprc
using account default from /home/asbesto/.msmtprc
host            = mail.xxx.org
port            = 25
timeout         = off
protocol        = smtp
domain          = localhost
auth            = choose
user            = [email]asbesto@xxx.org[/email]
password        = *
ntlmdomain      = (not set)
tls             = on
tls_starttls    = on
tls_trust_file  = /home/asbesto/.ssl/certs/xxxmsmtp.pem
tls_key_file    = (not set)
tls_cert_file   = (not set)
tls_certcheck   = on
tls_force_sslv3 = off
auto_from       = off
maildomain      = (not set)
from            = [email]asbesto@xxx.org[/email]
dsn_notify      = (not set)
dsn_return      = (not set)
keepbcc         = off
logfile         = /home/asbesto/.msmtp_log
syslog          = (not set)
reading recipients from the command line
<-- 220 xxx.org ESMTP Postfix (Debian/GNU)^M
--> EHLO localhost^M
<-- 250-xxx.org^M
<-- 250-PIPELINING^M
<-- 250-SIZE 10240000^M
<-- 250-VRFY^M
<-- 250-ETRN^M
<-- 250-STARTTLS^M
<-- 250-ENHANCEDSTATUSCODES^M
<-- 250-8BITMIME^M
<-- 250 DSN^M
--> STARTTLS^M
<-- 220 2.0.0 Ready to start TLS^M
Output of the delivery process
Bottom of message is shown.





I also tried to re-create the tls certs, as I used to do every time, in this way:


> 

mkdir -p ~/.ssl/certs

cd ~/.ssl/certs

wget [http://www.xxx.org/ca-xxx.cer](http://www.xxx.org/ca-xxx.cer)

openssl x509 -in ca-xxx.cer -out xxxmsmtp.pem




I'm really going NUTS for this! 

Yesterday at 18:00 I was able to send emails.
this morning, NO MORE:

> 

Nov 28 15:09:22 host=mail.xxx.org tls=on auth=on user=asbesto@freaknet.org from=asbesto@xxx.org recipients=corto@lalala.org mailsize=1527 exitcode=EX_OK

Nov 29 11:43:06 host=mail.xxx.org tls=on auth=on user=asbesto@xxx.org from=asbesto@xxx.org recipients=corto@lalala.org errormsg='TLS certificate verification failed: the certificate is not trusted' exitcode=EX_UNAVAILABLE



I upgraded some packages in my ubuntu, in particular, from my /var/log/apt/term.log I see:

> 

Preparing to replace libgnutls26 2.4.1-1build1 (using .../libgnutls26_2.4.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libgnutls26 ...

Setting up libgnutls26 (2.4.1-1ubuntu0.1) ...



Maybe some BUG in this new libgnutls26 library? 

Can anyone help me ?

I'm GONE NUTS.

Downgrading from libgnutls26-2.4.1-1ubuntu0.1 to libgnutls26-build1 SOLVED THE PROBLEM.

Now, some info:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505279](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505279)

It seem that this was a well common bug in Debian since November 11.

PLEASE, when upgrading a package, PLEASE DO THE BEST YOU CAN AS A DEVELOPER, BECAUSE USERS CAN GET VERY ANGRY! :( (please remember the infaust firefox 3 BETA included in a default ubuntu installation, what an HORROR)

---

