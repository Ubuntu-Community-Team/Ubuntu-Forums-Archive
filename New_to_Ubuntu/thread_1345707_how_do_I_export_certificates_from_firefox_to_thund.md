---
title: "how do I export certificates from firefox to thunderbird?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-04
hello,

I'm wondering if anyone knows of an easy way to export Firefox certificates to (for instance) desktop to then import them into Thunderbird.

Just clicked to accept a certificate at a public wifi connection (Firefox), and realized I should probably have saved the certificate somewhere to include it in the Thunderbird's certificate list. I haven't, and cannot remember the name of certificate. Thunderbird won't connect. 

Tried to select all the Firefox certificates, but when I click on export + save I see it doesn't let me to save them all at once: I have to save them one by one...don't have the time to do this...

thanks.

---

### Post by al.adab on 2009-12-05
No idea? 

I've just moved to my university library to do some work and the same thing happened. Can browse the internet with Firefox no problem, but Thunderbid won't connect. Again, it looks like it's a certificate issue. 

This time I haven't been asked to comply with a certificate - but then I might have been asked to in the past, and I can't remember, just that I've been using Thunderbird in the past week or so only...

---

### Post by al.adab on 2009-12-07
>bump<

---

### Post by al.adab on 2009-12-11
Could anyone kindly explain to me what to do when an email client refuses to fetch/send email when connected to certain networks? Exactly the same is happening with Claws Mail and Evolution. 

What kind of information do I need from the provider provider to make it work?

---

### Post by ukripper on 2009-12-11
who is your email provider?

---

### Post by al.adab on 2009-12-11
Gmail

---

### Post by ukripper on 2009-12-11
you shouldn't have any problem with gmail, evolution/thunderbird works great. Are you using POP or IMAP to pull emails?

---

### Post by al.adab on 2009-12-11
on IMAP. 

These email clients all work great but there are three places where I usually work where they don't. The connections at these places are public (no WEP access code) but you still need to be registered with them and the give you the HTTP Proxy + port for your browser. 

Hang on a sec...for the first time I've seen this error message (Claw Mail, installed yesterday): 

*can't connect to IMAP4 server: imap.gmail.com:993*

Should I actually be on an Gmail IMAP on a different port when I'm at these three places? Do you know what port? This might be the reason why also my Nokia's (Symbian) email client likewise doesn't fetch mail...

---

### Post by ukripper on 2009-12-11
> **al.adab said:**
> on IMAP. 

These email clients all work great but there are three places where I usually work where they don't. The connections at these places are public (no WEP access code) but you still need to be registered with them and the give you the HTTP Proxy + port for your browser. 

Hang on a sec...for the first time I've seen this error message (Claw Mail, installed yesterday): 

*can't connect to IMAP4 server: imap.gmail.com:993*

Should I actually be on an Gmail IMAP on a different port when I'm at these three places? Do you know what port? This might be the reason why also my Nokia's (Symbian) email client likewise doesn't fetch mail...

993 is standard port used by imap/pop settings for googlemail/gmail, it uses SSL encryption. That means if the connection doesn't support encryption it won't fetch your emails.

SMTP for sending out email uses STARTTLS, ports used are either 465 or 587.

---

### Post by al.adab on 2009-12-11
Need to contact the network people and find someone who can answer this...quite an ordeal. anyway...thanks for your feedback. It'd be great if gmail worked on an insecure IMAP connection as well...

---

### Post by al.adab on 2009-12-12
OK - went to the library help desk and...they claim their network does support encryption (well, I got stuck as they said "as you can see Outlook works with Gmail...")...have no idea, haven't used Windows for ages...

...anyway, I'm giving it a try with Opera...are we sure it's not a matter of certificates? At the help desk that's the first think the IT people mentioned...

---

### Post by al.adab on 2009-12-14
same thing with Opera. The browser's fine but it won't download any email.

---

### Post by ukripper on 2009-12-15
you can try this thunderbird addon - [https://addons.mozilla.org/en-US/thunderbird/addon/6381](https://addons.mozilla.org/en-US/thunderbird/addon/6381) which should configure your gmail settings accordingly. See if that makes difference.


And here is more details on thunderbird configuration with gmail [http://mail.google.com/support/bin/answer.py?answer=78892&topic=12761&hl=en#](http://mail.google.com/support/bin/answer.py?answer=78892&topic=12761&hl=en#)

---

### Post by harshanahnd on 2010-01-17
You need to import that certificate in to Thunderbird and edit its trust settings. 

Find the certificate and import it (Edit > Preferences > Advanced > Certificates > View certificates)

On authorities tab import it and click edit. And under "Edit trust settings" place ticks to edit.

---

