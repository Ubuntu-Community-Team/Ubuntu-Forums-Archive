---
title: "Simple way to send email"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by FoolInTheRain on 2009-03-29
Hi all,

Is there an easier way than Postfix to send mail from a ubuntu server if all I want to do is send the emails from the server to an external ISP for delivery?

thanks!

---

### Post by MountainX on 2009-03-29
yes, I recently installed ssmtp and configured it to send mail via my google account. It was very easy compared to Postfix, but also more limited, of course.

---

### Post by MountainX on 2009-03-29
Here are my notes:

References:
[http://www.sysadminsjourney.com/2008/09/01/use-gmail-as-an-smtp-relay-using-ssmtp](http://www.sysadminsjourney.com/2008/09/01/use-gmail-as-an-smtp-relay-using-ssmtp)
[http://blogs.techrepublic.com.com/security/?p=440](http://blogs.techrepublic.com.com/security/?p=440)
[http://www.linuxquestions.org/questions/linux-software-2/ssmtp-works-partly-710382/#post3470299](http://www.linuxquestions.org/questions/linux-software-2/ssmtp-works-partly-710382/#post3470299)
[http://wiki.freebsd.org/SecureSSMTP](http://wiki.freebsd.org/SecureSSMTP)  (security – use this!)

sudo apt-get install ssmtp mailx

sudo nano /etc/ssmtp/ssmtp.conf 
# Debug=Yes 
# 
# Config file for sSMTP sendmail 
# 
# The person who gets all mail for userids < 1000 
# Make this empty to disable rewriting. 
# root=postmaster 
root=me@gmail.com 

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com 
mailhub=smtp.gmail.com:587 
UseSTARTTLS=yes 
UseTLS=yes 
AuthUser=myotheraccount@gmail.com 
AuthPass=password

# Where will the mail seem to come from? 
rewriteDomain=mydomain.com 

# The full hostname 
hostname=MyServer 

# Are users allowed to set their own From: address? 
# YES - Allow the user to specify their own From: address 
# NO - Use the system generated From: address 
#FromLineOverride=YES

---

### Post by FoolInTheRain on 2009-03-30
Thank YOU !!   :)

---

### Post by hyper_ch on 2009-03-30
postfix is easy :)

---

