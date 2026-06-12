---
title: "Sending Nagios notifications with Postfix through Gmail"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Maclor on 2010-11-10
I have been trying to set up Postfix to send me notifications through Gmail for a couple days now and I've gotten to a point were I'm completely lost. I've found varies guides to help but now in my log it tries to authenticate using "USER@email@gmail.com". I'm pretty sure it is just 1 setting somewhere that is causing it to add the user I am logged into Ubuntu with to the front of the email address for authentication.

I am running Ubuntu 10.10 with most up to date postfix and nagios. 

Main.cf
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname =domain.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = gmail.com, wsd.local, Nagios-ubuntu, localhost.localdomain, localhost
relayhost = smtpd_tls_key_file =
smtp_use_tls = yes
relayhost = [smtp.gmail.com]:587

## TLS Settings
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
#
## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = no
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpd


```End of Mail.log
```

Nov 10 08:21:46 Nagios-ubuntu postfix/pickup[6691]: 35B8146709: uid=0 from=<root>
Nov 10 08:21:46 Nagios-ubuntu postfix/cleanup[14994]: 35B8146709: message-id=<20101110142146.35B8146709@domain.local>
Nov 10 08:21:46 Nagios-ubuntu postfix/qmgr[10103]: 35B8146709: from=<root@email1@gmail.com>, size=274, nrcpt=1 (queue active)
Nov 10 08:21:46 Nagios-ubuntu postfix/local[14996]: warning: database /etc/aliases.db is older than source file /etc/aliases
Nov 10 08:21:47 Nagios-ubuntu postfix/local[14996]: 35B8146709: to=<email2@gmail.com>, relay=local, delay=1.3, delays=0.97/0.17/0/0.15, dsn=5.1.1, status=undeliverable (unknown user: "email2")
Nov 10 08:21:47 Nagios-ubuntu postfix/cleanup[14994]: 159F04670A: message-id=<20101110142147.159F04670A@domain.local>
Nov 10 08:21:47 Nagios-ubuntu postfix/bounce[14997]: 35B8146709: sender delivery status notification: 159F04670A
Nov 10 08:21:47 Nagios-ubuntu postfix/qmgr[10103]: 35B8146709: removed
Nov 10 08:21:47 Nagios-ubuntu postfix/qmgr[10103]: 159F04670A: from=<>, size=1760, nrcpt=1 (queue active)
Nov 10 08:21:47 Nagios-ubuntu postfix/error[14999]: 159F04670A: to=<root@email1>, orig_to=<root@email1@gmail.com>, relay=none, delay=0.36, delays=0.12/0.15/0/0.09, dsn=4.7.1, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.gmail.com[74.125.113.109] said: 535-5.7.1 Username and Password not accepted. Learn more at                   ?535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 y8sm185328vch.5)


```Thanks.

---

### Post by Maclor on 2010-11-10
Thought I saw a problem with aliases so I changed a little there to make it like so.

```

# See man 5 aliases for format
postmaster:    email1@gmail.com
root:        email1@gmail.com
nagios:        email1@gmail.com
root@nagioswsd:    email1@gmail.com

```

My log now looks like this 

```
Nov 10 09:06:46 Nagios-ubuntu postfix/qmgr[19960]: 424C646709: from=<root@email1@gmail.com>, size=274, nrcpt=1 (queue active)
Nov 10 09:06:47 Nagios-ubuntu postfix/local[20064]: 424C646709: to=<btrittin@gmail.com>, relay=local, delay=1.3, delays=0.77/0.27/0/0.23, dsn=5.1.1, status=undeliverable (unknown user: "email2")
Nov 10 09:06:47 Nagios-ubuntu postfix/cleanup[20060]: 247CE46710: message-id=<20101110150647.247CE46710@domain.local>
Nov 10 09:06:47 Nagios-ubuntu postfix/bounce[20065]: 424C646709: sender delivery status notification: 247CE46710
Nov 10 09:06:47 Nagios-ubuntu postfix/qmgr[19960]: 424C646709: removed
Nov 10 09:06:47 Nagios-ubuntu postfix/qmgr[19960]: 247CE46710: from=<>, size=1760, nrcpt=1 (queue active)
Nov 10 09:06:47 Nagios-ubuntu postfix/tlsmgr[20068]: warning: request to update table btree:/var/run/smtpd_tls_session_cache in non-postfix directory /var/run
Nov 10 09:06:47 Nagios-ubuntu postfix/tlsmgr[20068]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix
Nov 10 09:06:47 Nagios-ubuntu postfix/tlsmgr[20068]: warning: request to update table btree:/var/run/smtp_tls_session_cache in non-postfix directory /var/run
Nov 10 09:06:47 Nagios-ubuntu postfix/tlsmgr[20068]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix

```

Not really sure where to go from here with the unknown user: "email2". Any help is greatly appreciated.

---

### Post by SlugSlug on 2010-11-10
nvm

---

### Post by SlugSlug on 2010-11-10
remove this line
root@nagioswsd:    [email]email1@gmail.com[/email]

and run
sudo newaliases

---

### Post by SlugSlug on 2010-11-10
in terminal run

```
sendmail valid@email.addrress
```type some stuff

hit ctrl+d to send & exit


then show log again

---

### Post by Maclor on 2010-11-10
```

Nov 10 09:19:17 Nagios-ubuntu postfix/smtp[21305]: A26FB4670F: to=<root@email1>, orig_to=<root@email1@gmail.com>, relay=smtp.gmail.com[74.125.91.109]:587, delay=1.5, delays=0.11/0.06/1.3/0, dsn=4.7.1, status=deferred (SASL authentication failed; server smtp.gmail.com[74.125.91.109] said: 535-5.7.1 Username and Password not accepted. Learn more at                   ?535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 k15sm743637qcu.35)
Nov 10 09:22:34 Nagios-ubuntu postfix/pickup[21303]: 9823146715: uid=0 from=<root>
Nov 10 09:22:34 Nagios-ubuntu postfix/cleanup[21813]: 9823146715: message-id=<20101110152234.9823146715@domain.local>
Nov 10 09:22:34 Nagios-ubuntu postfix/qmgr[21302]: 9823146715: from=<root@email1@gmail.com>, size=287, nrcpt=1 (queue active)
Nov 10 09:22:35 Nagios-ubuntu postfix/local[21815]: 9823146715: to=<email2@gmail.com>, relay=local, delay=12, delays=11/0.2/0/0.13, dsn=5.1.1, status=bounced (unknown user: "email2")
Nov 10 09:22:35 Nagios-ubuntu postfix/cleanup[21813]: 251CF46716: message-id=<20101110152235.251CF46716@domain.local>
Nov 10 09:22:35 Nagios-ubuntu postfix/qmgr[21302]: 251CF46716: from=<>, size=1976, nrcpt=1 (queue active)
Nov 10 09:22:35 Nagios-ubuntu postfix/bounce[21816]: 9823146715: sender non-delivery notification: 251CF46716
Nov 10 09:22:35 Nagios-ubuntu postfix/qmgr[21302]: 9823146715: removed
Nov 10 09:22:36 Nagios-ubuntu postfix/smtp[21818]: 251CF46716: to=<root@nagioswsd>, orig_to=<root@email1@gmail.com>, relay=smtp.gmail.com[74.125.91.109]:587, delay=1.1, delays=0.1/0.19/0.77/0, dsn=4.7.1, status=deferred (SASL authentication failed; server smtp.gmail.com[74.125.91.109] said: 535-5.7.1 Username and Password not accepted. Learn more at                   ?535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 k15sm746663qcu.35)

```

Fixed the old aliases problem but still getting that [email]root@email1@gmail.com[/email]. That's 1 problem fixed though.

This line is bothering me too but I'm not sure what to make of it. 

Nov 10 09:22:35 Nagios-ubuntu postfix/local[21815]: 9823146715:  to=<email2@gmail.com>, relay=local, delay=12,  delays=11/0.2/0/0.13, dsn=5.1.1, status=bounced (unknown user: "email2")

---

### Post by SlugSlug on 2010-11-10
not sure -- 

try follow this guide
[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)

seen this comment

"" my password was not sent to gmail using the sasl_passwd example. when leaving out the brackets it worked.
 *example
 does not work:
[smtp.gmail.com]:587 [EMAIL="sername@gmail.com"]sername@gmail.com[/EMAIL]: Password  -- no spave after the :  -- it put a smiley face
 works fine:
smtp.gmail.com:587 [EMAIL="sername@gmail.com"]sername@gmail.com[/EMAIL]: Password 
 Thanks for a great guide! ""

---

### Post by Maclor on 2010-11-10
Oddly enough that is the exact guide I followed. Didn't see that comment though but I tried that and it didn't work. May just try redoing the whole guide and seeing what happens. Thanks for the help though. Definitely appreciated.

---

### Post by SlugSlug on 2010-11-10
cool, hope you get it sorted, wasn't long back I did my postfix.. I bought a domain and set up my pc to use that address for mail / web etc..  was great when it finally worked with encryption and all that jazz.

---

### Post by toekneewood on 2010-11-10
I have done this one lots of times and it works for me give this a go :-)
Install applications
```

sudo apt-get install openssl mutt

```

Create authentication file to send via google
```

touch ~/.muttrc ; nano ~/.muttrc

```


Paste the following into "~/.muttrc"  Make sure you change the following (YOUR-USER-NAME, YOURPASSWORD & Your Real Name)
```

set imap_user = "YOUR-USER-NAME@gmail.com"
set imap_pass = "YOURPASSWORD"
 
set smtp_url = "smtp://YOUR-USER-NAME@smtp.gmail.com:587/"
set smtp_pass = "YOURPASSWORD"
set from = "YOUR-USER-NAME@gmail.com"
set realname = "Your Real Name"
 
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

```

Command to send the html or txt message from the command line
```

mutt -e "my_hdr Content-Type: text/html" -s "Test" someones-email-address@hotmail.com < message.html
or
echo "Test" | mutt -s Hello someones-email-address@hotmail.com

```

---

### Post by Maclor on 2010-11-10
Well that got a message to my gmail inbox. Hopefully Nagios won't require me to change anything in the notifications. Testing that now. If it matters I'm using Centreon to manage Nagios.

Edit: It appears that Nagios didn't send the email. It looks like it is still trying to use postfix. How can I change my mailer or the service for it to use mutt?


The command for service-notify-by-email if it matters.

/usr/bin/printf "%b" "***** centreon Notification *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $DATE$ Additional Info : $SERVICEOUTPUT$" | @MAILER@ -s "** $NOTIFICATIONTYPE$ alert - $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$

---

### Post by SlugSlug on 2010-11-10
Out of curisioty.. why are you using Centreon to control Nagios?  I've recently installed Nagios... found it great - so am wondering what input this Centreon  has?

---

### Post by Maclor on 2010-11-10
No real reason besides back in school when we set up Nagios we used another program to control it and my buddy recommended Centreon. Pretty much it. It's working great and the interface was really easy to learn so far so I can't really complain about it.

---

### Post by Maclor on 2010-11-10
Think I found my real problem now that I know mutt is working.

I tried changing my service-notify-by-email to a hard coded message. And it didn't work even though when I pasted it into terminal it sent the email just fine. This is the command I used "/usr/bin/printf "TEST" |/usr/bin/mutt -x -s "TEST" [email]email2@gmail.com[/email]"" without the beginning and ending quotes.

I tested the plugin and got the following error on that notification command and others I didn't change.


[IMG]http://192.168.0.125/centreon/img/icones/16x16/note.gif[/IMG]  Plugin test 		Command Line/usr/bin/printf \&\#34\ 		OutputPlugin has to be in : /usr/local/nagios/libexec 		Status


So how can I fix this?

---

