---
title: "Pulling mail from another mailhost (live.com) to a mail server running Ubuntu?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by hawkeyex on 2009-07-20
Can I run a mail server that will have the capability to pull my mail from another server (mail.live.com for example) and use the localhost mail server to send out email (if any)

I want to be able to run my own spam filters on it - probably RBL-related stuff.

Some pointers or starters would be great!

David

---

### Post by llamabr on 2009-07-20
Yes, if live.com allows pop or imap.  Isn't it just hotmail, though?  I seem to remember hotmail being very jealous with their mail, allowing neither.

---

### Post by hawkeyex on 2009-07-21
Yes, I can POP live.com (and I do that with Thunderbird)

How do I do that using a mail server set up here in Ubuntu - doesn't matter what mail server program I use. I'm flexibile as long as I can use RBLchecks to filter mails

---

### Post by llamabr on 2009-07-24
well, if you don't care, I use pine with spamassassin.  Checking over imap.

---

### Post by apmcd47 on 2009-07-24
> **hawkeyex said:**
> Yes, I can POP live.com (and I do that with Thunderbird)

How do I do that using a mail server set up here in Ubuntu - doesn't matter what mail server program I use. I'm flexibile as long as I can use RBLchecks to filter mails

I''ve never used it myself but it sounds like you want [procmail]("http://en.wikipedia.org/wiki/Procmail"), which is in the Ubuntu repositories.

Andrew

---

