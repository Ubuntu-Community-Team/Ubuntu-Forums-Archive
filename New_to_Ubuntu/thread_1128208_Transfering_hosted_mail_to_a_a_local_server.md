---
title: "Transfering hosted mail to a a local server"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Saghaulor on 2009-04-17
Since September 2008 we have been hosting our email via a web-hosting service. We need to begin to archive our email for compliance sake, and we believe that having the email in house would be the best solution to accomplish that goal.

Also we are planning on switching web-hosts next month. As I understand it, we would lose all of our mail upon switching. Consequently, we need a solution to download that mail, and host it locally.

Is there a way to download the mail from everyone's mailbox, and then add it to our current server?

My first idea was to download each mailbox into mbox format, and then hopefully it could be designated as the mailbox on the server for each mail user. 

I don't really know much about this, any help would be appreciated.

---

### Post by Bachstelze on 2009-04-17
If you have POP or IMAP access to the remote malboxes, you can fetch the messages to the local mailboxes using [font="monospace"]fetchmail[/font].

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/mail-fetchmail.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/mail-fetchmail.html)

---

### Post by Saghaulor on 2009-04-17
Thanks Hymntolife.

Just for clarification sake, when it's fetching mail to the local mailboxes, it means the local boxes on the mail server, and not the mailbox on the mail user client?

---

### Post by Bachstelze on 2009-04-17
Yes, it means the local mail boxes on the mail server. Then, if you want your users to be able to access their mail from outside, you'll have to install a POP and/or IMAP server on your mail server.

---

### Post by Saghaulor on 2009-04-17
I know that it's possible to incorporate spam/virus filtering into your mail server. That would be something that I would like to implement as well. Additional things to implement would be content filtering and mail archiving. 

One thing that is highly annoying is that our current email host doesn't offer any sort of spam filtering. My Blackberry pulls my email, which means that on a day like today, where I'm getting blasted constantly, my Blackberry is going nuts.

Also, we used to use Exchange before last September. Our Exchange server crashed, but we have backups of the files. I'm wondering if there is a way incorporate the old exchange boxes into the new mail boxes?

Could you make some suggestions?

---

### Post by Bachstelze on 2009-04-17
A very good spam filter is SpamAssassin, I can't tell you exactly how to set it up since my own mail server runs FreeBSD, but I'm sure Google knows a lot about it. I heard clamav is a good antivirus, but I never felt the need to implement it myself. As for Exchange, no idea either.

---

### Post by llamabr on 2009-04-17
Spamassassin is a nice choice, and it runs just fine in bsd.

I'm skeptical about using fetchmail for this, since presumably you would have to do it for each user.

How many users do you have?  And do you have admin access to the server where the mail is currently located?

---

### Post by Bachstelze on 2009-04-17
> **llamabr said:**
> Spamassassin is a nice choice, and it runs just fine in bsd.

I know. ;) I was just saying I couldn't help about setting it up in Ubuntu since I don't run it on Ubuntu myself.

---

### Post by Saghaulor on 2009-04-17
> **llamabr said:**
> Spamassassin is a nice choice, and it runs just fine in bsd.

I'm skeptical about using fetchmail for this, since presumably you would have to do it for each user.

How many users do you have?  And do you have admin access to the server where the mail is currently located?

We're talking about approximately 20-30 users. I have admin access to the remote server. 

What about POP3Aggregator? 

Please forgive my ignorance, I'm reading up as much as I can, but I'm very new to this end of the business. My email server background is limited to MS Exchange, and not much of that either.

---

