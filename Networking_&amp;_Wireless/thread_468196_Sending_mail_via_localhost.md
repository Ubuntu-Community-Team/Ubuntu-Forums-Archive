---
title: "Sending mail via localhost"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by endersshadow on 2007-06-08
I want to be able to just send mail via my local machine.  I don't want to go through external SMTP servers, but I also don't have a domain for my machine.  Is there a way where I could just set up my computer to serve as a local SMTP server?  I don't need an entire mail server, just the SMTP.  Reasoning for this is that my current SMTPs are sometimes very fickle, so I'd just like to make things easier on myself by making it local.

Thanks!

---

### Post by Mr. C. on 2007-06-08
The question is not "can" but "may".

You can setup an SMTP server.  However, your ISP may block outbound port 25 to all but their servers.  In addition, many SMTP servers block attempts to send mail from dynamic or residential IP ranges, and from SMTP servers that do not have valid A / PTR records.

MrC

---

### Post by endersshadow on 2007-06-08
And how would I set it up?

---

### Post by Mr. C. on 2007-06-08
You can use any of several SMTP mailers.  I use postfix, but others are exim, sendmail, etc.

For postfix, install the postfix package and configure away.

You'll have to give up on the idea that you just install a package and all will be fine.  Configuring and running and email server is not trivial.

MrC

---

### Post by endersshadow on 2007-06-08
> **Mr. C. said:**
> You can use any of several SMTP mailers.  I use postfix, but others are exim, sendmail, etc.

For postfix, install the postfix package and configure away.

You'll have to give up on the idea that you just install a package and all will be fine.  Configuring and running and email server is not trivial.

MrC

I never thought that it was trivial.  I'm not of the opinion that it's just a simple install, I'm well aware that there are configurations that I have to change.  My biggest problem is this: How do I configure postfix to use the localhost but without a domain name to use as the server name?

---

### Post by Mr. C. on 2007-06-08
Install postfix. 

See: [http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone)

The follow the link: "Postfix on hosts without a real Internet hostname" 

This describes what you want.

MrC

---

### Post by endersshadow on 2007-06-09
> **Mr. C. said:**
> Install postfix. 

See: [http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone)

The follow the link: "Postfix on hosts without a real Internet hostname" 

This describes what you want.

MrC

Many thanks :)

---

### Post by sica07 on 2007-07-20
> **Mr. C. said:**
> Install postfix. 

See: [http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#stand_alone)

The follow the link: "Postfix on hosts without a real Internet hostname" 

This describes what you want.

MrC

Hello! I want to do the same thing as endersshadow, so I looked at the link you provided. It say that I must use the  generic address mapping. But there is no generic folder or file in my postfix folder. :( I have Postfix ver. 2.3.3. I reinstalled and  ... no generic. Were to look for it? Thx

---

### Post by Mr. C. on 2007-07-20
If you look a little further at lines 1 - 7, its shows the addition/change to your main.cf file and the generics table you create.  its just a file.  Create it as per your needs according to the instructions on that page.

MrC

---

