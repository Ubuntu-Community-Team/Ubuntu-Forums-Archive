---
title: "[SOLVED] install and configure sendmail in localhost"
date: 2016-02-26
forum: Networking &amp; Wireless
---

### Post by biagiopas on 2016-02-26
Hello everybody,
I'm trying, so far unsuccessfully, to install sendmail smtp on developing laptop with ubuntu14.04 desktop, so to send email from php,

I followed this step by step guide for the installation of sendmail
[http://lukepeters.me/blog/getting-the-php-mail-function-to-work-on-ubuntu](http://lukepeters.me/blog/getting-the-php-mail-function-to-work-on-ubuntu)
the file /etc/hosts file now looks like this
127.0.0.1 localhost
127.0.1.1 pcl-biagio
127.0.0.1 localhost localhost.localdomain pcl-biagio
...
where "pcl-biagio" is my hostname in ubuntu

php.ini
sendmail_path = /usr/sbin/sendmail -i -t
mail.log = /var/log/apache2/phpmail.log

The mail () function returns false and does not send

php mail.log shows no errors

however some errors are displayed by the sendmail service

biagio@pcl-biagio:/etc$ sudo service sendmail start
* Starting Mail Transport Agent (MTA) sendmail 554 5.0.0 /etc/mail/sendmail.cf: line 1: unknown configuration line "LOCAL_CONFIG"
451 4.0.0 /etc/mail/sendmail.cf: line 2: fileclass: cannot open 'ATURE(masquerade_envelope)LOCAL_CONFIG': No such file or directory
451 4.0.0 /etc/mail/sendmail.cf: line 4: fileclass: cannot open 'ATURE(use_cw_file)FEATURE(use_ct_file)FEATURE(smrsh)MAILER_DEFINITIONS': No such file or directory
554 5.0.0 /etc/mail/sendmail.cf: line 5: MAILER(local)MAILER(smtp): A= argument required
554 5.0.0 /etc/mail/sendmail.cf: line 6: unknown configuration line "LOCAL_CONFIG"
554 5.0.0 No local mailer defined
554 5.0.0 QueueDirectory (Q) option must be set

$ sudo service sendmail status
MTA: is not running
QUE: Same as MTA

any suggestions?

---

### Post by blueridgedog on 2016-02-27
It is complaining about an error in your sendmail.cf file.  I suggest you post it.

---

### Post by biagiopas on 2016-02-27
hi [**[COLOR=#000000]blueridgedog[/COLOR]**]("http://ubuntuforums.org/member.php?u=459469") thankyou for answer 
/etc/mail/sendmail.cf filecontent (ps: "pcl-biagio" is so hostname)
```

LOCAL_CONFIG
FEATURE(masquerade_envelope)LOCAL_CONFIG
Cwpcl-biagio
FEATURE(use_cw_file)FEATURE(use_ct_file)FEATURE(smrsh)MAILER_DEFINITIONS
MAILER(local)MAILER(smtp)
LOCAL_CONFIG
## Custom configurations below (will be preserved)

VERSIONID($Id: starttls.m4,v 8.14.4-4.1ubuntu1 2014-02-11 13:02:08 cowboy Exp $)
VERSIONID($Id: autoconf.m4, v 8.14.4-4.1ubuntu1 2014-02-11 13:02:08 cowboy Exp $)
### /etc/mail/sendmail.mc ###
# LOCAL_CONFIG
# FEATURE(`masquerade_envelope')dnl
# LOCAL_CONFIG
# Cwpcl-biagio
# FEATURE(`use_cw_file')dnl
# FEATURE(`use_ct_file')dnl
# FEATURE(`smrsh')dnl
# dnl #
# dnl # Dialup/LAN connection overrides
# dnl #
# include(`/etc/mail/m4/dialup.m4')dnl
# include(`/etc/mail/m4/provider.m4')dnl
# dnl #
# MAILER_DEFINITIONS
# MAILER(local)dnl
# MAILER(smtp)dnl
# 
# LOCAL_CONFIG
# ## Custom configurations below (will be preserved)
# 
# #reabiagio
# #enable sendmail to use STARTTLS
# include(`/etc/mail/tls/starttls.m4')dnl



```

---

### Post by SeijiSensei on 2016-02-27
I don't have any line called LOCAL_CONFIG in any of my sendmail.mc files.

Also every line must end with "dnl" like this:
```
FEATURE(masquerade_envelope)dnl
```

In addition, don't use the hash character ("#") to comment out lines in an m4 file.  Use "dnl" at the beginning of lines you want to comment out.

```
dnl This is a comment.
```

After everything is set, you'll need to rebuild sendmail.cf by navigating to the directory where sendmail.mc is stored and running
```
sudo m4 < sendmail.mc > sendmail-new.cf
```
Review sendmail-new.cf in a text editor to make sure it looks okay, then replace the existing sendmail.cf with the contents of sendmail-new.cf and restart the sendmail daemon.

---

### Post by biagiopas on 2016-02-27
thankyou for answer SeijiSensei

> you'll need to rebuild sendmail.cf
LOCAL_CONFIG it is in my sendmail.mc too #-o
then rebuild sendmail.cf did not work for me

problem solved by uninstall and then reinstall sendmail
now sendmail service starts and sends emails
 no idea why :o

---

### Post by SeijiSensei on 2016-02-29
I just went back and read your earlier comment, and it seems that you had the m4 file, sendmail.mc, somehow renamed to sendmail.cf.  If you haven't looked at both files after reinstallation, I suggest you do so, since they look nothing alike.

Also, please go to "Thread Tools" at the top of this page and marked the thread "SOLVED".

---

