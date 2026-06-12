---
title: "Copy/Move emails in IMAP Thunderbird account to Gmail.com account"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by hanzj on 2011-04-29
Hello,

So we access an IMAP account using Thunderbird. But now, I would like to copy the emails into a gmail.com account. 

I know that I can, one by one, forward each email, but that's tedious and will mess up the "from" email address.


Any help?

Thank you.

---

### Post by Leppie on 2011-04-29
you could either try the import function in gmail, or setup your gmail account in thunderbird and copy the folders over to your gmail account.

---

### Post by hanzj on 2011-05-02
The import function in gmail.com (in the Accounts & Import tab in [https://mail.google.com/mail/?shva=1#settings/accounts](https://mail.google.com/mail/?shva=1#settings/accounts)) only imports from POP accounts, not from IMAP).

---

### Post by hanzj on 2011-05-25
leppie,

I tried your copy-over tip in Thunderbird and it worked. Here's what I did. 
1. Get both accounts on thunderbird.
2. Select the message or the folder. 
3. Right-click. Choose Move To/...



My question: How does Thunderbird do that? I checked the original source (headers) of one email that was transferred from one email account (account1) to another (account2) and it doesn't appear that the message was re-emailed. When I search the headers/source of the message for the keyword "account2", I don't see any "account2" text.

---

