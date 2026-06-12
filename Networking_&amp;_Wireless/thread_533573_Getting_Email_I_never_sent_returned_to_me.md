---
title: "Getting Email I never sent returned to me"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by gnottage on 2007-08-24
OK, so I have a server at home, which does my personal Email. I use fetchmail to grab it from a few different POP3 mailboxes and then deliver it with postfix into my maildir. Dovecot then serves it to me using IMAP.

Now, I think it's nothing to do with me, but some spammers have cottoned on to using my domain name as a fake from address, so I'm now getting loads of failure messages and similar (Undelivered Mail Returned to Sender | failure notice | Delivery Status Notification (Failure) | Returned mail: see transcript for details) coming into my own mailbox that catches all the Email for the domain. I want to keep catching all Email since if anyone misspelt an address I'd like to get it, but I don't want to have the hassle of manually deleting the replies saying Email I never sent is spam. ideally I want it to disappear, but I'm not sure how. Does anyone have any advice on what I can do?

---

### Post by heimo on 2007-08-24
> **gnottage said:**
>  Does anyone have any advice on what I can do?

This won't solve it, but helps a bit: Configure SPF. 
[http://www.openspf.org/](http://www.openspf.org/)
[http://en.wikipedia.org/wiki/Sender_Policy_Framework](http://en.wikipedia.org/wiki/Sender_Policy_Framework)

---

### Post by spoonman184 on 2007-08-24
I know nothing of this sort of thing, but seeing as how the spam is using the domain you chose, would you be able to change your domain?

Also, could the spam find your domain name using the other services you described to reroute mail?

---

### Post by gnottage on 2007-08-24
I've looked into SPF and hopefully enabled it for the domain. Time will tell if it does help things...

I've been using this domain for over 7 years, and don't want to change it.

---

### Post by callan79 on 2007-08-24
> **gnottage said:**
> I've looked into SPF and hopefully enabled it for the domain. Time will tell if it does help things... I've been using this domain for over 7 years, and don't want to change it.

Hello,

I work for an Internet provider here in Australia, and probably twice a week I'll have a customer ask me the same question.

Answer 1 - ignore it, as in a few weeks they'll move onto someone else's domain and the problem will go away.

Answer 2 - make sure you have not got a "wildcard" set up on your domain - i.e. a catch all account that grabs mail for [email]anything@yourdomain.com[/email]. This used to be a good idea, these days it just attracts spam. Set up your server to bounce any mail that does not exactly match your address.

Cheers :)
Callan

---

### Post by gnottage on 2007-08-24
Looks like SPF has helped, the DNS TXT record is live and there are hardly any messages coming in now... Hopefully the spammers will be getting their spam returned to them. Thanks for everyone's help with this - I hope the problem doesn't appear for anyone else!

---

