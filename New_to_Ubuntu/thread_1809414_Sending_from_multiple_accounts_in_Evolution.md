---
title: "Sending from multiple accounts in Evolution"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by jermza on 2011-07-21
Let's say I have three email accounts coming into my Gmail account (including my Gmail address).  Gmail has a lovely option to send mail as another one of your accounts (other than Gmail).  This is great because all my mail is in one location.

But I want to use Evo and not the Gmail interface.

Instead of setting up multiple accounts in Evo, all my mail is arriving in my Gmail inbox, which is thus arriving in my Evo IMAP inbox.  One location for all sent and received messages.

However, I'd like to reply to certain emails from one of my accounts other than Gmail.  The only way I can do this, it seems, is to add new accounts.  But the problem is that I don't want to create more inboxes and split my mail.  I simply want to reply to a message and change my From account.

Is this possible?

---

### Post by gzarkadas on 2011-07-21
You could create the accounts, but arrange for not receiving messages by providing a bogus incoming server name at the account dialog box. 

Alternatively, if this cannot be done (for example, the account on question is a POP account that requires to connect to the incoming POP server to authenticate before sending a mail) you could arrange to leave a copy of each message to the server, so that it will arrive in your google mailbox too. Then create a filter to delete all such incoming messages.

You could also create a filter to send copies of any outgoing messages to google mailbox also, so that you have both received and sent messages there.

---

### Post by jermza on 2011-07-22
> You could create the accounts, but arrange for not receiving messages by  providing a bogus incoming server name at the account dialog box. 
Wouldn't that return errors every time the client checks for mail?

> Alternatively, if this cannot be done (for example, the account on  question is a POP account that requires to connect to the incoming POP  server to authenticate before sending a mail) you could arrange to leave  a copy of each message to the server, so that it will arrive in your  google mailbox too. Then create a filter to delete all such incoming  messages.

POssible, except that it will create turmoil with which messages have been read and not read, especially when using my mobile device.

The more I think about this, the more I think it's not possible...

---

### Post by jermza on 2011-07-22
I think I've worked it out.

What about setting up the other accounts as per normal, but, in the settings, uncheck all options relating to receiving mail?

Does that make sense?

---

