---
title: "Sendmail Cron Error"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Jloser on 2010-08-20
I configured my server to be able to automatically email me via a gmail account.  Once per hour I get the following message:

```
fromMail Submission Program <ww********il@gmail.com>
toroot

dateThu, Aug 19, 2010 at 4:40 PM
subjectCron <smmsp@ww******> test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp
mailed-bygmail.com

/usr/share/sendmail/sendmail: 1248: /usr/sbin/sendmail-msp: not found
```

I am unsure of what it means, or how to stop this email from being sent out.  Any help?

---

### Post by Jloser on 2010-08-20
In the file /etc/cron.d/sendmail there were only two lines that were not commented out.

```
#MAILTO=root
#*/20 *    *    *    *          smmsp   test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp
```

I commented out both, and the message seems to have stopped.  What functionality am I now missing out on?

---

### Post by MikeFlint on 2011-01-26
I think this issue comes from installing a variety of MTAs none of which is completely able to remove the previous one (or more likely, we haven't correctly removed the old one!)

The problem arises because they all try to appear like 'sendmail' and thus pollute the sendmail directories.  I experienced this problem when installing POSTFIX. Sendmail is in there by default, and postfix takes on most of its job, but there are parts that of sendmail still trying to run. But postfix has installed itself within parts of send/sendmail sufficient to make what's left of sendmail fail.

In the observed case here, the sendmail (original) is still putting its entries in cron to run, although it itself has mostly been usurped in its roll. And hence the errors. Commenting out the CRON entry is only a short-term fix, as it's likely on your next server re-load that crontab will be re-built at boot time.

You should:

1. Edit the sendmail.conf file at /etc/mail/ to leave blank the two variables "MSP_INTERVAL" and "QUEUE_INTERVAL"
2. Run (as sudo) /usr/sbin/sendmailconfig   which re-builds the cron entries from your updated config - effectively creating an empty crontab.

This should mean your fix holds over a server re-boot.

-------

I think there is to some extent issues with the way Linux (Ubuntu) tests for installed components. As here, merely testing that an executable exists doesn't mean necessarily that that system is being used. I've had similar issues with cron thinking anacron is doing the work, simply because the anacron executable exists (the "text -x usr/sbin/anacron" in the system crontab)  ... when in reality anacron hasn't been configured to run, so you end up with no cron jobs running.

---

### Post by airblade on 2011-04-13
I experienced these errors after installing POSTFIX and DOVECOT.
It seems that *apt* did not remove the OLD sendmail files (just the sendmail-bin).
To fix this I did the following:
```

sudo apt-get --purge remove sendmail-base sendmail-cf sendmail-doc

```
This removed any remaining files for the old sendmail (including /etc/cron.d/sendmail witch causes this error message).

Running Ubuntu 10.04 LTS

> **Jloser said:**
> I commented out both, and the message seems to have stopped.  What functionality am I now missing out on?
You are not missing out any functionality if you have postfix supplying sendmail binaries.
If you on the other hand would like to use plain sendmail you have to install sendmail-bin:
```

sudo apt-get install sendmail-bin

```
This installs plain sendmail binaries and removes postfix.

---

