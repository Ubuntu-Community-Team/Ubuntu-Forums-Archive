---
title: "evolution auto-reply?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by wizard10000 on 2009-07-14
Hi, forum -

I make pretty extensive use of Evolution's filters to keep the twits out of my inbox - does anyone know of a way I can use Evolution to autoreply to a filtered message?

I'd like for Evolution to respond with something like "welcome to my killfile" so folks that don't take the hint when I don't respond actually get something in return so they'll quit sending emails.

Not a big deal, just wondering if there was some way to enhance my twit filter a little bit.

thanks -

---

### Post by niteshifter on 2009-07-14
Hi,

Mark 'em as junk and never see 'em again.

---

### Post by wizard10000 on 2009-07-14
> **niteshifter said:**
> Hi,

Mark 'em as junk and never see 'em again.

Hadn't thought of that.  Thanks  :)

---

### Post by Paddy Landau on 2009-07-14
> **wizard10000 said:**
> I'd like for Evolution to respond with something like "welcome to my killfile" so folks that don't take the hint when I don't respond actually get something in return so they'll quit sending emails.
Nearly all spam is automatically generated and emailed.

Responding to spam simply confirms that you've read the message, which means that you'll get triple the amount of spam. No human will actually read your message.

Never, ever respond to spam.

---

### Post by LewRockwell on 2009-07-14
> **Paddy Landau said:**
> Nearly all spam is automatically generated and emailed.

Responding to spam simply confirms that you've read the message, which means that you'll get triple the amount of spam. No human will actually read your message.

Never, ever respond to spam.

MOST CERTAINLY...THIS!!!!

oh, and if you know your neighbor is a spammer...please convey our extreme animosity and displeasure at their continual assaults on our inboxes!

.

---

### Post by wizard10000 on 2009-07-16
Nah - not spam, real email from from real morons.  Spam's easy to handle  :)

---

### Post by Paddy Landau on 2009-07-16
> **wizard10000 said:**
> I'd like for Evolution to respond with something like "welcome to my killfile" so folks that don't take the hint when I don't respond actually get something in return so they'll quit sending emails.
If I received a reply like that, I'd wonder what the heck you were talking about. It certainly wouldn't work as a hint for me.

Have you considered not hinting but actually asking to be removed from their distribution list? After all, a non-reply isn't a hint; it's nothing.

---

### Post by lisati on 2009-07-17
> **wizard10000 said:**
> 
I'd like for Evolution to respond with something like "welcome to my killfile" so folks that don't take the hint when I don't respond actually get something in return so they'll quit sending emails.


**Caution:** some spammers and other morons use forged "From" and "Reply-to" information in the email headers - *blindly responding to them is a risky business, you don't want to be reported as a spammer*. I've lost count of the junk emails where the supposed "from" address displays as one of my own. Sometimes it could be an innocent third-party who gets the reply. I've even had bounced email reports for emails I never sent out.

I'm currently thinking of starting a project which can use Evolution's "run a program" option for filtered email (which is how I chanced upon this thread). The basic idea, which is stil only partly formed, is to apply some intelligence to the process of choosing who gets an automatic reply to email, whether it's a polite "go away", a "please read and acknowledge my terms and conditions" or a semi-automatic spam report.

Edit/Note: some morons don't respond well to "Thank you for your email. Please read my website for the details you request." and persist in pestering you for information that that could easily obtain through publicly available information such as phone books.

---

### Post by Paddy Landau on 2009-07-17
> **lisati said:**
> **Caution:** some spammers and other morons use forged "From" and "Reply-to" information in the email headers
Absolutely correct. Bouncing such emails frequently hurts innocents.

> **lisati said:**
> I'm currently thinking of starting a project which can use Evolution's "run a program" option for filtered email (which is how I chanced upon this thread). The basic idea, which is stil only partly formed, is to apply some intelligence to the process of choosing who gets an automatic reply to email, whether it's a polite "go away", a "please read and acknowledge my terms and conditions" or a semi-automatic spam report.
Such a program would suffer the same shortfalls as even the best spam blockers (Google's one springs to mind): It will have some false positives and false negatives. As such, it will sometimes respond to a spammer's check and therefore verify your address as valid (giving you tons more spam); it will sometimes respond negatively to a genuine emailer.

---

### Post by lisati on 2009-07-17
> **Paddy Landau said:**
> Absolutely correct. Bouncing such emails frequently hurts innocents.


Such a program would suffer the same shortfalls as even the best spam blockers (Google's one springs to mind): It will have some false positives and false negatives. As such, it will sometimes respond to a spammer's check and therefore verify your address as valid (giving you tons more spam); it will sometimes respond negatively to a genuine emailer.

True: I might shift my focus a little, having abandanoed a couple of "challenge-response" spam filters in Windows some time back due to people not really knowing what to do with them (as well as the risk of being reported as a spammer myself). I'm not writing off the "run a program" option, and I'm thinking that maybe some kind of logging might be the way to go, where data is stored locally instead of being part of an autoresponder.

---

