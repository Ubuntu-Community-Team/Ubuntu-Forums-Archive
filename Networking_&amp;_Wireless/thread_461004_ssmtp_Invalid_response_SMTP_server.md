---
title: "ssmtp: Invalid response SMTP server"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by lduperval on 2007-06-01
Hi,

I am using procmail and ssmtp to filter messages and forward them as needed.

I have noticed that in my forwarding process, I sometimes get this error in the log:

ssmtp: Invalid response SMTP server

What happens then is that the message seems to be lost. It is not queued for resend or anything like that.

Is there a way I can have resends be done automatically with ssmtp? Or do I need to go to a heavyweight solution such as qmail or sendmail?

I don't want a daemon sitting by listening. What I need is:

[LIST]
[*]Some way to forward emails to my ISP's mail hb
[*]Some automatic error recovery (so a message is resent until it goes through)
[*]No daemon running
[*]Some way to check that there are no pending messages upon reboot
[/LIST]

Thanks,

L

---

### Post by andrew.46 on 2007-07-05
Hi,

 What are the contents of your /etc/ssmtp/ssmtp.conf file?

                    Andrew

---

### Post by lduperval on 2007-07-06
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=myhub.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=localhost

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

---

### Post by andrew.46 on 2007-07-07
Hi,

 ssmtp sems a little under-configured. Have a look at:

[http://people.aapt.net.au/~adjlstrong/mutt.html#ssmtp](http://people.aapt.net.au/~adjlstrong/mutt.html#ssmtp)

 for an example. The configuration on this page is for Gmail but it will give you an idea. If you run the command:

```
man ssmtp.conf
```

you will see an explanation of many of the settings.

   Al the best,

         Andrew

---

### Post by lduperval on 2007-07-08
Nope, there isn't anything there that I can add to implement a retry mechanism. It looks like I will need to go the Postfix way or something.

Thanks for the help,

L

---

