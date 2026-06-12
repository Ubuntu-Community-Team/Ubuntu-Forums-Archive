---
title: "Using Yahoo in Evolution Mail"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by jlhaslip on 2009-04-28
I had found a Topic about the use of Gmail in the Archives and could not post to it because of the Archive Status, so I am creating a new Topic to explain the settings for Yahoo! mail that work for me in Evolution.

Reference: [http://ubuntuforums.org/showthread.php?t=128763](http://ubuntuforums.org/showthread.php?t=128763) 

In the Evolution settings found at Edit > Preferences > select an existing or create a new Evolution Mail account: 

Identify Tab:

Name: Name of Folder in Evolution
Full Name: Your name here (your personal name, not Yahoo! user name)
Email Address: [email]your_yahoo_user_name@yahoo.ca[/email]

Receiving Email tab :

Server type: POP
Server: pop.mail.yahoo.ca
Username: [email]yourname@yahoo.ca[/email]
Use secure connection: SSL encryption
Authentication type: Password
Remember password: checked (optional)


Under Sending Mail tab:

Server type: SMTP
Server: smtp.mail.yahoo.ca
Server requires authentication: checked
Use secure connection: SSL encryption
Authentication type: Plain
Username: yourname
Remember password: checked (optional)


These are the settings I have for Yahoo! and it works for me. Notice that this works for a dot CA yahoo account, but it should work fine in a dot COM as well.

Moderators: Please move as required. ie: can this be added to the above referenced Archive Topic? 

Thanks.

---

### Post by lisati on 2009-04-28
My $0.02:

I use a couple of yahoo.co.nz email accounts. Yahoo's help pages tell me to use pop.mail.yahoo.co.nz and smtp.mail.yahoo.co.nz, with settings for SSL etc as outlined by the OP. I've found that the servers pop.mail.yahoo.com.au and smtp.mail.yahoo.com.au work just as well for my accounts, and have, on a couple of occasions, actually worked better.

---

### Post by emeraldgirl08 on 2009-06-10
Wish there was a simpler way of syncing my email with evolution!

I don't have a paid POP account w/ Yahoo. I'm having problems with fetching mail. I get an error.

I'm confused on yourusername and your name. Are they both the (your name)@yahoo.com or are they both different? 

If anyone has an easier solution so that I can fetch mail from Google, Excite, and Yahoo I'd appreciate some suggestions.

:KS

---

### Post by blackxored on 2009-06-10
I usually use fetchmail and fetchyahoo and the evolution account is Maildir. It has worked pretty well, also on Live Mail and other services not providing direct pop/imap access.

Hope its helps.

---

### Post by emeraldgirl08 on 2009-06-10
Where would I get the fetchmail and fetchyahoo?

---

### Post by philinux on 2009-06-10
Only works for paid for accounts like mail plus.

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html)

---

### Post by halitech on 2009-06-10
> **philinux said:**
> Only works for paid for accounts like mail plus.

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-14.html)

unless you are a Canadian and have a yahoo.ca account and then it works without having a paid account.

---

### Post by philinux on 2009-06-10
> **halitech said:**
> unless you are a Canadian and have a yahoo.ca account and then it works without having a paid account.

Lucky guys then.

---

### Post by halitech on 2009-06-10
> **philinux said:**
> Lucky guys then.

in some ways, not with our governments right now though :(

---

### Post by misswham on 2009-06-29
Is yahoo allowing syncing with evolution on free accts now? if so how do i set it up?

---

### Post by LewRockwell on 2009-06-29
> **misswham said:**
> Is yahoo allowing syncing with evolution on free accts now? if so how do i set it up?

short answer=no

brief answer=not in the Amerikan Empire

long answer=redacted for brevity...

.

---

