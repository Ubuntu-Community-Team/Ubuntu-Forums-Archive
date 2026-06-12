---
title: "cannot sent email using smtp.streamyx.com with evolution email client"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by wstay on 2009-12-17
I am using Ubuntu 8.10 Intrepid.
I am using Evolution for my email client.
I can receive email using pop.streamyx.com.
My problem is I cannot sent email using smtp.streamyx.com.
The error message is: 
´Could not connect to smtp.streamyx.com: Connection timed out´.
But when I sent the same email using Outlook email client, there is no problem sending the email.
Does this mean that my isp does not support using Evolution to send email?
Can someone please help and explain?

---

### Post by wesleybailey on 2009-12-18
When was the last time you tested sending an email from outlook? 
According to this [http://www.streamyx.com.my/whats_new/whats_new.php?id=article_20080311](http://www.streamyx.com.my/whats_new/whats_new.php?id=article_20080311)

Streamyx is blocking access on port 25.

If your are able to send an email with outlook right now, then we need to take a look at your settings.

Please let me know.

---

### Post by wstay on 2009-12-18
> **wesleybailey said:**
> When was the last time you tested sending an email from outlook? 
According to this [http://www.streamyx.com.my/whats_new/whats_new.php?id=article_20080311](http://www.streamyx.com.my/whats_new/whats_new.php?id=article_20080311)

Streamyx is blocking access on port 25.

If your are able to send an email with outlook right now, then we need to take a look at your settings.

Please let me know.

Thanks for your information.
I did sent an email with outlook because I see my email disappearing from my outbox and appearing in my send folder.
So I thought I had sent an email successfully.
But today I check my email and I receive the following message:

"Your message did not reach some or all of the intended recipients.
Subject:Michelin 4x4 Diamaris Tires - 275/55R19
Sent:17/12/2009 16:26
The following recipient(s) could not be reached:
'wholesale@discountedwheelwarehouse.com' on 17/12/2009 16:26
553 5.3.0 <wholesale@discountedwheelwarehouse.com>... Authentication required. Please refer to http://webmail.tm.net.my/smtpauth.html"

---

### Post by wesleybailey on 2009-12-18
It might be possible to use smtp.streamyx.com, try setting up the smtp to use authentication.

In Evolution
1. Click on Edit -> Prefrences
2. Select your email account and then click Edit -> Sending Email
3. Choose "server requires authentication" and put in your streamyx username and password.

Now try to send yourself an email as a test, and trying sending an email to a different domain, to test functionality.

---

### Post by wstay on 2009-12-20
> **wesleybailey said:**
> It might be possible to use smtp.streamyx.com, try setting up the smtp to use authentication.

In Evolution
1. Click on Edit -> Prefrences
2. Select your email account and then click Edit -> Sending Email
3. Choose "server requires authentication" and put in your streamyx username and password.

Now try to send yourself an email as a test, and trying sending an email to a different domain, to test functionality.

I tried to send an email to myself and got this error message:
¨Could not connect to smtp.streamyx.com: Connection timed out¨

---

### Post by diablo75 on 2009-12-20
If you're getting a "Connection timed out" error, then it means, very plainly, that the connection is not being established due to some sort of networking related reason and I would suspect this reason is that the ISP you're connecting through is blocking the default port.

Is it possible that you could contact your hosting service or check their FAQ page for information about an alternative port number?  If you can find one, just append your smtp server address like this:

smtp.streamyx.com:###

Just add a colon and the port number immediately after the address and evolution will use that port instead of the default.  The same goes for your incoming address, but you probably won't need to change it if it's working already.

I know I have to do this with my host (Lunarpages) because my ISP blocks the defaults... and because I enabled SSL encryption so my email is transmitted more securely to my computer.

---

