---
title: "Multiple Websites, One Machine - Email relay?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by protogenesis on 2008-07-29
I'm hosting two different websites on my machine - one IP address, two websites.  I have [www.mysite.org](www.mysite.org) and [www.mysite.com](www.mysite.com)

mysite.org is the name of the machine.  I can receive/send email without problem.  Can also see its webpage.

mysite.com is the newly (as of last night) hosted site on my machine.  I can see the webpage I set up for this site, no problem.  I can send email, but cannot, alas, receive.  

I received the error message back almost immediately:

workhost.com #5.7.1 smtp;554 5.7.1 <user@mysite.org>: Relay access denied>

Obviously, this means that my linux box doesn't relay email from mysite.org to mysite.com despite them both being on the same machine.  So, I'm not quite sure how to set up my box so that any mail going to 'me@mysite.com' gets to me and doesn't end up being rejected.

Oh, running Postfix if that helps -- I'm assuming I'll be tweaking something there to allow 'relaying'

---

