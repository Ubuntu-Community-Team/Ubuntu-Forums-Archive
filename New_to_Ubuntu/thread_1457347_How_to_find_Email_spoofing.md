---
title: "How to find Email spoofing?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-18
Nowadays spammers use fake email addresses to send a mail,it appears to be a real mail..How to identify email spoofing?and how to protect email spoofing?

---

### Post by J V on 2010-04-18
Send a reply and ask if its them... Unfortunately, unless someone signs a message with a PGP key theres no way currently to identify them automatically.

---

### Post by kolinab on 2010-04-18
I disagree with the above advice. Replying to a possibly fradulent or spoofed address might just confirm to the sender that their email reached your eyes . . . I think that means you might get more spam/phishing attempts in the future.

I'm not a security expert. MY basic advice is that I make sure *I'm* the one initiating any contact with my bank, etc. Don't trust links in email, and never enter passwords or login details to anything from a link followed from am email.

I did a little google search and found this basic page on phishing security. It's a decent start.

[http://www.focus.com/fyi/it-security/44-ways-protect-phishing/](http://www.focus.com/fyi/it-security/44-ways-protect-phishing/)

K

---

### Post by Chronon on 2010-04-19
I think J V forgot the <sarcasm> tags.

---

### Post by lisati on 2010-04-19
Care and wisdom is needed. Spammers often use forged "from" addresses, and you don't want to be tagged as a spammer yourself if you accidentally annoy innocent third parties.

---

### Post by Mykk on 2010-04-19
> **J V said:**
> Send a reply and ask if its them... Unfortunately, unless someone signs a message with a PGP key theres no way currently to identify them automatically.

What ever you do DON'T do this. 

Replying to emails that you may think are fake/spoofed is incredibly stupid. Theres only one thing to do and thats DELETE!

---

### Post by Paddy Landau on 2010-04-19
You are correct that spammers and scammers fake their email addresses.

Unfortunately, they often use real email addresses that they've harvested from forums and other websites.

My email address is one of those, so my email address has been used as the 'from' address on spam. The unfortunate side-effect is that I often get returned emails that I never sent, and some people don't get my (genuine) emails because my email address has been marked as a spammer.

If you have a spam or scam email, **do not reply to it**. If it's a scam, you could forward it to the applicable bank or other organisation so that they know about it (they usually have a dedicated email address for scam emails and try to get the offending websites shut down), but in any case delete the email.

Just as real life comes with mosquitoes and con artists, so modern Internet life comes with spam and scam. At the moment, there is no reliable way to deal with them. Use something like Thunderbird or Google Mail with their junk filters, and apply your common sense.

---

### Post by ScottinSoCal on 2010-04-19
As others have pointed out, there's no way to automatically identify a spoofed e-mail. But once you've identified an e-mail as spoofed, you can sometimes track down who really sent it.

In the headers (show all of them) there are lines that tell you where the e-mail came from. You can trace back everywhere it's been and where it originated from. If the spammer really did his homework, he used an open relay that doesn't log the originating IP address. Those aren't nearly as common as they used to be, because just being an open relay is enough to get your domain blacklisted these days. Anyway, if you've got the originating IP address, you can trace it at least to whoever is assigned to it. A complaint to their ISP can take care of it.

---

### Post by Zintha on 2010-04-19
> **kolinab said:**
> I disagree with the above advice. Replying to a possibly fradulent or spoofed address might just confirm to the sender that their email reached your eyes . . . I think that means you might get more spam/phishing attempts in the future.

I'm not a security expert. MY basic advice is that I make sure *I'm* the one initiating any contact with my bank, etc. Don't trust links in email, and never enter passwords or login details to anything from a link followed from am email.

I did a little google search and found this basic page on phishing security. It's a decent start.

[http://www.focus.com/fyi/it-security/44-ways-protect-phishing/](http://www.focus.com/fyi/it-security/44-ways-protect-phishing/)

K
I won't read more of this topic after reading this, its the way its done.

Don't ever presume you won something online, don't ever click on a link from your bank/credit card/ X account if they say you need to  sort something out etc.

If you get an email from somewhere you have an account and it seems legit then click your bookmark and login that way. Don't use the links in the emails at any point.
Its a good practice to get into. 

Even so, a lot of junk filters catch out a lot of spam emails these days, so be especially careful if you're like me and you occasionally surf the junk-inbox.

---

### Post by Paddy Landau on 2010-04-19
> **ScottinSoCal said:**
> |A complaint to their ISP can take care of it.
I understand that most of the *real* servers are held by the spammers themselves in locations outside legal prevention, e.g. Russia where spamming appears to be legal.

But as you say, spammers and scammers often use means (often illegal) to hide their real origin. You may find that the spam originated from some unwitting sucker whose Windows computer has a hidden bot on it, sending the spam and getting him blacklisted.

---

### Post by J V on 2010-04-19
If it is a scammer they will be using a real adress, in that case don't reply, just delete.

If its a spammer they will probably be spoofing (Much easier to make fake from header than to make an account past all the captchas etc) so replying will help notify whoever is being spoofed of this. (Make sure reply header is same as from header)

But yes, its probably better to just delete it all...

---

### Post by Gaweph on 2010-04-19
Am I being stupid or cant you just look at the header to see where the email originated, I dont think this can be faked, as it shows where an email has been passed through.

I.E. you can say you are from [email]help@paypal.com[/email], but your header wont say you came from paypal.com?

is thisnot correct??

Gaw

---

### Post by Paddy Landau on 2010-04-19
> **J V said:**
> If it is a scammer they will be using a real adress
No, not necessarily. It depends on various factors.

> **Gaweph said:**
> Am I being stupid or cant you just look at the header to see where the email originated, I dont think this can be faked, as it shows where an email has been passed through.
For the lay person, like you and me, that's true. But more sophisticated spammers do indeed fake this. Or, they use viruses to get innocent people's computers to do the dirty work for them.

---

