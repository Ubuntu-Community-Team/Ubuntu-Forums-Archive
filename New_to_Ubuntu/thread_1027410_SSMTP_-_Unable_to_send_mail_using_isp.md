---
title: "SSMTP - Unable to send mail using isp"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Frank_F on 2009-01-01
Hello,

Unable to send email in command line using my isp provider



frank@name-desktop:/etc/ssmtp$ ssmtp [email]name@rogers.com[/email]
From: [email]name@rogers.com[/email]
To: [email]name@rogers.com[/email]
Subject: Test Subject
This is the body
ssmtp: 553 From: address not verified; see [http://www.rogershelp.com/verify-email](http://www.rogershelp.com/verify-email)


SSMTP.CONF

frank@frank-desktop:/etc/ssmtp$ cat ssmtp.conf
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=f.falco@rogers.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.broadband.rogers.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=frank-desktop

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

AuthUser=name
AuthPass=password
#AuthMethod=CRAM-MD5

---

### Post by jboy012000 on 2009-01-01
Why don't you send your e-mails via Evolution, or Thunderbird.

---

### Post by chrisod on 2009-01-01
Are you trying to use your own mail server to send mail? Most ISPs block that as part of their anti-spam efforts.

---

### Post by Frank_F on 2009-01-01
I would love to use Evolution, but I am hoping to use the command line...so that I can send mail in a shell script (ie. Hardrive is full...send myself and email)

Thanks

---

### Post by Frank_F on 2009-01-01
Hi I dont have any mail server set-up, simply installed SSMTP...thanks

---

### Post by chrisod on 2009-01-01
SSMTP is an SMTP mail server. Most ISPs will only send mail that originates with their mail server. You will need to use some mail client (Thunderbird, Evolution, whatever) and configure it so send mail via the SMTP server designated by your ISP. If you don't want to install anything use whatever webmail your ISP provides, or Gmail, or Yahoo Mail, etc.

---

