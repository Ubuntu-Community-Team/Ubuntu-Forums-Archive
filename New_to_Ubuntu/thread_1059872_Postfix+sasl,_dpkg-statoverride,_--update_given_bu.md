---
title: "Postfix+sasl, dpkg-statoverride, --update given but /var/spool/postfix/var/run/saslau"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by batfastad on 2009-02-04
Hi everyone

I'm experimenting with setting up a virtual private server to act as a private email relay for our email newsletters.

I want to secure postfix with SASL so was following this tutorial... [http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582) but I've run into a problem.

At the stage: Now we should reconfigure SASL to change it's root directory and place it in Postfix's chroot
I tried running the suggested command
```
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```

But I get the following error:
--update given but /var/spool/postfix/var/run/saslauthd does not exist

So it looks like there's a mistake somewhere, or my VPS environment is different to that used in the tutorial.
Should I change the command to read: /var/spool/postfix or /var/run/saslauthd?

Anyone know how to solve this?

Cheers, B

---

### Post by apjone on 2009-02-04
sudo mkdir -p /var/spool/postfix/var/run/saslauthd would create the directory. 

REF: [http://78.47.159.34/virtual_postfix_mysql_quota_courier_p2](http://78.47.159.34/virtual_postfix_mysql_quota_courier_p2)

---

