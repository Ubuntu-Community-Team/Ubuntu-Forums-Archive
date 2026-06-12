---
title: "problems with thunderbird"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by period3 on 2009-04-29
I'm having problems setting up thunderbird.  

I use IMAP.  My account name is  [email]firstname.lastname@myserver.com[/email]...   My SMTP server is something.different.com, and my IMAP server is mail.myserver.com.

In thunderbird, I enter the following:
Server Name: mail.myserver.com
User Name: firstname.lastname
Account Name: firstname.lastname@myserver.com

When I check my mail, it tries to log me on as firstname.lastname@mail.myserver.com instead of firstname.lastname@myserver.com.

It seems it automatically appends the 'server name' to my user name, which is wrong.   If I change username to firstname.lastname@myserver.com, then it tries to log me in as firstname.lastname@myserver.com@mail.myserver.com....

How can I specify a login name manually, with no automatic appending?

I'm using Ubuntu 8.10, thunderbird 2.0.0.21

---

### Post by Celauran on 2009-04-29
> **period3 said:**
> I'm having problems setting up thunderbird.  

I use IMAP.  My account name is  [email]firstname.lastname@myserver.com[/email]...   My SMTP server is something.different.com, and my IMAP server is mail.myserver.com.

In thunderbird, I enter the following:
Server Name: mail.myserver.com
User Name: firstname.lastname
Account Name: [email]firstname.lastname@myserver.com[/email]

When I check my mail, it tries to log me on as [email]firstname.lastname@mail.myserver.com[/email] instead of [email]firstname.lastname@myserver.com[/email].

It seems it automatically appends the 'server name' to my user name, which is wrong.   If I change username to [email]firstname.lastname@myserver.com[/email], then it tries to log me in as [email]firstname.lastname@myserver.com@mail.myserver.com[/email]....

How can I specify a login name manually, with no automatic appending?

I'm using Ubuntu 8.10, thunderbird 2.0.0.21
Are the logins actually failing, though? It always shows that it's trying to connect as username@servername, so [email]bob.smith@gmail.com@imap.gmail.com[/email] (for instance) is actually correct.

---

### Post by period3 on 2009-04-29
Ah, you're right, it works now. Thanks!


> **Celauran said:**
> Are the logins actually failing, though? It always shows that it's trying to connect as username@servername, so [email]bob.smith@gmail.com@imap.gmail.com[/email] (for instance) is actually correct.

---

