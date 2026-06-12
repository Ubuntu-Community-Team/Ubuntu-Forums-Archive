---
title: "Yahoo mail"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by theozzlives on 2009-04-23
I can get Yahoo mail on my cell, and people can get Gmail in Evolution. Can I get Yahoo mail in Evolution and how?

---

### Post by billgoldberg on 2009-04-23
I don't think so.

---

### Post by PaulReaver on 2009-04-23
Yes you can if your cell phone supports pop3.  

Sign in to your Yahoo Mail account. 
Click the Options. 
Then click "POP & FORWARDING". 
Then click "setup or edit pop forwarding".  
Then on the Pop Access and Forwarding screen tick "web and pop access". 

Also if you click the "pop settings" and it'll tell you what you'll need to punch into your cell phone.

Click save its at the bottom of the screen, And thats you halfway done, you just need to set up you cell phone.

One of the cell phone forums would be a better place to ask about setting the phone up.:P

---

### Post by PaulReaver on 2009-04-23
Check here. hope it helps.

[http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html]("http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html")

Ignore the stuff about needing a yahoo mail plus account. Even the free accounts support pop3

---

### Post by Agent.Logic_ on 2009-04-23
I think theozzlives is asking about getting Yahoo! mail via evolution in the computer. The POP3 and SMTP settings for Yahoo! mail and other email services can be found here: [http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html). But if I'm correct, you need to be a premium user to use Yahoo! mail's POP service.

---

### Post by PaulReaver on 2009-04-23
Sorry about before. done an all nighter.

Sign in to your Yahoo Mail account.
Click the Options.
Then click "POP & FORWARDING".
Then click "setup or edit pop forwarding".
Then on the Pop Access and Forwarding screen tick "web and pop access".

Click save,  its at the bottom of the screen, And thats you halfway done, you just need to set up your evolution.

then follow this guide
[http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html]("http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html")


I've got a free Yahoo account and i use thunderbird to check my emails.

---

### Post by apmcd47 on 2009-04-23
> **Agent.Logic_ said:**
> I think theozzlives is asking about getting Yahoo! mail via evolution in the computer. The POP3 and SMTP settings for Yahoo! mail and other email services can be found here: [http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html). But if I'm correct, you need to be a premium user to use Yahoo! mail's POP service.

Yahoo give the information on their web pages - go to the *POP Access and Forwarding* page from the webmail page, and click on *[POP Settings]*.

Maybe it's different for yahoo.co.uk users, but I'm pretty sure I'm **not** a Premium user, and I've got it going on *Thunderbird* on both Windows and Linux.

Andrew

---

### Post by mark.giblin on 2009-04-23
Yahoo operate on "Non standard ports" and impose auth login requirements.

---

### Post by PaulReaver on 2009-04-23
log in to your yahoo mail account.
 switch to yahoo mail classic and enable the "pop and forwarding" in the options.

then add these settings to evolution,thunderbird, outlook, etc..

yahoo mail settings

POP Mail Server= pop.mail.yahoo.com
port= 995
use ssl

SMTP server= smtp.mail.yahoo.com
port= 465
use ssl

---

### Post by PaulReaver on 2009-04-23
look

[http://www.neowin.net/news/main/09/03/04/yahoo-readying-free-pop3-access]("http://www.neowin.net/news/main/09/03/04/yahoo-readying-free-pop3-access")

---

### Post by Ms_Angel_D on 2009-04-23
If the above options don't work for you there is always YPops! I've been using it for a while now and it works splendidly 

[http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/)

---

### Post by theozzlives on 2009-04-26
none of the above worked and Ypops repository is down.

---

### Post by theozzlives on 2009-05-15
Bump!

---

### Post by NHArticleTen on 2009-05-15
> **theozzlives said:**
> Bump!

I just checked on Yahoo Mail Options and in the United States you need to pay Yahoo for their "Mail Plus" service($19.95yr) to have POP access to your email.

My solution: Gmail

---

