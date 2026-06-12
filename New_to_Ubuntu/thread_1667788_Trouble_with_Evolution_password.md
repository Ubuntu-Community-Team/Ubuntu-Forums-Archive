---
title: "Trouble with Evolution password"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by L Campbell on 2011-01-15
I'm running 10.10 on a PC and just set up an account on Evolution.

Under 'Authentication Type', I clicked on the up/down arrows and made a selection, checked remember password, then composed an email.

When I tried to send the email I was told to enter a password, which I did (it was not the same as what I had selected under 'password')and my mail will not 'send'. 

I would appreciate it if you would advise me how to unscrew my screwup.

TIA

---

### Post by gordintoronto on 2011-01-15
Evolution uses a hidden folder called .evolution to save everything. You should be able to start over by deleting that folder.

Have you used this email account before? Some ISPs have little quirks in their email setup.

---

### Post by theozzlives on 2011-01-15
> **L Campbell said:**
> I'm running 10.10 on a PC and just set up an account on Evolution.

Under 'Authentication Type', I clicked on the up/down arrows and made a selection, checked remember password, then composed an email.

When I tried to send the email I was told to enter a password, which I did (it was not the same as what I had selected under 'password')and my mail will not 'send'. 

I would appreciate it if you would advise me how to unscrew my screwup.

TIA

Could be the wrong settings:
Incoming is normally pop3
Outgoing is normally smtp

Most ISPs don't use a password protected connection for smtp

---

