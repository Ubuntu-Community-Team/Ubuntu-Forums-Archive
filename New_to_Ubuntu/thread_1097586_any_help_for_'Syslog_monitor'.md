---
title: "any help for 'Syslog monitor'"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by sazan on 2009-03-16
I was browsing for a method to monitor **syslog** and notify me about any kernel error (like **KERN_ALERT**) and i found  written somewhere that _there are many software packages available to monitor them and send the notifications of any event via beep of the PC speaker, call a pager, send e-mail, etc. automatically._

I have searching for quite a time now and couldn't encounter any such package. 

Does anyone know about such packages. 

Any help is appreciated.

---

### Post by billgoldberg on 2009-03-16
> **sazan said:**
> I was browsing for a method to monitor **syslog** and notify me about any kernel error (like **KERN_ALERT**) and i found  written somewhere that _there are many software packages available to monitor them and send the notifications of any event via beep of the PC speaker, call a pager, send e-mail, etc. automatically._

I have searching for quite a time now and couldn't encounter any such package. 

Does anyone know about such packages. 

Any help is appreciated.

A "simple" script should be able to do that.

Google around untill you find a similar script and modify it.

---

### Post by sazan on 2009-03-16
Thanks for the response, 

I am not good at scripting though I will try to see how this thing can be implemented. I was looking if someone has already done anything on it. !!!

---

### Post by orethrius on 2009-03-16
You might find something of a starting point in sendEmail (it's a Perl script).

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

### Post by sazan on 2009-03-16
> **orethrius said:**
> You might find something of a starting point in sendEmail (it's a Perl script).

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

Thanks for the link, but my focus is more towards the beep and if possible mobile (sms)

---

### Post by orethrius on 2009-03-16
> **sazan said:**
> Thanks for the link, but my focus is more towards the beep and if possible mobile (sms)
I've been messing around with this quite a bit.  You are aware of what happens when you email phonenumber AT telco DOT com|net|org|whatever?  Try it and see.  ;)

As for the system beep, I believe there's an escape character that does a system bell, but I'm pretty sure that's also a C thing.

---

### Post by sazan on 2009-03-16
> **orethrius said:**
> I've been messing around with this quite a bit.  You are aware of what happens when you email phonenumber AT telco DOT com|net|org|whatever?  Try it and see.  ;)


This sounded interesting, but i didn't get anything when i tried emailing to my number !!!! :(

---

### Post by orethrius on 2009-03-16
> **sazan said:**
> This sounded interesting, but i didn't get anything when i tried emailing to my number !!!! :(
Well, it's the FULL number, including any area codes, and your telco may require more - assuming they support it.  It comes in handy with those companies that do. :-D

---

### Post by sazan on 2009-03-16
hmm... i did give my full number with country code to all (i.e. net|org|com) , got mail error for all except for net and haven't got any sms yet !!

hav u tried it out ??:o

---

### Post by orethrius on 2009-03-16
> **sazan said:**
> hmm... i did give my full number with country code to all (i.e. net|org|com) , got mail error for all except for net and haven't got any sms yet !!

hav u tried it out ??:o
Again, not all telcos support it.  I know for a fact that AT&T does - at least Stateside - but I can't speak for anyone else.  It's cool when it works, but if it doesn't it's not.  Out of curiosity, what telco are you using?  They often throw a subdomain in there just to screw people up (like chat, or message, or txt - mine is [email]number@**txt**.att.net[/email])

Here's a post that I hope is of some use:
[http://www.livejournal.com/tools/textmessage.bml?mode=details](http://www.livejournal.com/tools/textmessage.bml?mode=details)

That only really covers international carriers, though.  If you're using a regional carrier (such as Airtel), it might be listed here:
[http://gleez.com/articles/sms/email-to-mobile-send-sms-freely-india](http://gleez.com/articles/sms/email-to-mobile-send-sms-freely-india)

Here's hoping one of those works...

---

