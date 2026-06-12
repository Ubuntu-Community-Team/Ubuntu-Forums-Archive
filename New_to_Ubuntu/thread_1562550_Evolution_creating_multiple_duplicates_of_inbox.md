---
title: "Evolution creating multiple duplicates of inbox"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-27
Every once in a while Evolution makes a duplicate of all of my Hotmail inbox.  This does not effect my professional IMAP email, only my POP3 Hotmail account.   I now have 11 copies of every email in my inbox, and two copies were generated today while I was at work.

Why does this happen and how do I stop it from happening?

---

### Post by jtarin on 2010-08-27
That's a configuration setting on your Hotmail account. You need to go there and tell it how to handle forwarding for POP mail. You should also look at Evolution and set it to mirror your instructions on Hotmail. It seems you have it downloading mail that you haven't read, but its not deleting or marking as read, so not to download again. You have to sync the behavior.

---

### Post by outleradam on 2010-08-28
I sync my email to my iPhone and my evolution.  iPhone does not have a problem. Evolution keeps downloading duplicates

Why would I want it to delete from the server?  Hotmail allows 2 gigs of service.  Why can't evolution handle it like it does with my imap server?

---

### Post by outleradam on 2010-08-30
Bump!   Why does Evolution keep duplicating my email from a pop3 server?

---

### Post by Jonny87 on 2010-08-30
I've had this as well and found it fustrating. The way that I've gotten around it is by going in to the web client settings and reconfiguring my settings for pop from scratch etc. Then getting evolution to start again with an empty inbox. Also if you can, set up you web client to move the mail to another location such as archives or something after pop/imap forwarding. That way theres still a copy on the server but once evolution has grabed it, it won't be still in the inbox next time it looks.

I know with my email. It doesn't matter if its marked read or not, I can gon online and view my emails and as long as I keep them in the Inbox, evolution will still download them.

---

### Post by outleradam on 2010-09-01
So this is a confirmed bug in evolution.

---

