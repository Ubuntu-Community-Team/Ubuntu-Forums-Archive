---
title: "Postfix/Courier problems"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by Uzelth on 2008-01-29
Heya,

I recently followed a howto ([http://howtoforge.net/virtual-users-domains-postfix-courier-mysql-roundcube-ubuntu-6.06](http://howtoforge.net/virtual-users-domains-postfix-courier-mysql-roundcube-ubuntu-6.06)) on my gutsy VPS.

The installation, etc went fine, everything starts but whenever I try to access the mailserver via Kontact/KMail I get a "Temporary problem, please try again later" error... Via SquirrelMail I get a "Connection dropped" error.

Any ideas what the problem might be?

---

### Post by PaulFr on 2008-01-30
In testing my authorization issues with the Falko Postfix guide on howtoforge.net (**[http://howtoforge.net/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://howtoforge.net/virtual-users-and-domains-with-postfix-ubuntu-7.10)**, very similar to the HowTo you followed) I found that:

1. Changing the crypt=1 to crypt=0 in the > vi /etc/pam.d/smtp step, and

2. Changing the following lines in the > vi /etc/courier/authmysqlrc step from > MYSQL_CRYPT_PWFIELD password
#MYSQL_CLEAR_PWFIELD password to > # MYSQL_CRYPT_PWFIELD password
MYSQL_CLEAR_PWFIELD password helped a lot.

Please note in this case, the MySQL table should store the cleartext password for the test user accounts. Once you have verified that this works without encryption, you can then turn on encryption for the password field.

---

