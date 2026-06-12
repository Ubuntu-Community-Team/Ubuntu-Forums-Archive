---
title: "Evolution Mail won't send"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by exkend on 2009-11-29
I have inserted all the necessary details into the Account Editor and have been able to receive messages but not send. I have stumbled upon a few related threads that have recommended adding the port number to the outgoing server configuration. This hasn't help and after messing around with various settings( as well as restoring them back), I haven't found a way to send.

I am using:Ubuntu 9.10 64, mail2world, settings are: 

pop3.mail2world.com & imap4.mail2world.com

Receiving is set to password
Sending is set to Login

Any help or suggestions would be appreciated

Ex

---

### Post by Temposs on 2009-11-30
For sending, you need an smtp server, not pop3 or imap. You should find out what is the address of mail2world's smtp server and change your settings appropriately.

---

### Post by dcstar on 2009-11-30
> **exkend said:**
> I have inserted all the necessary details into the Account Editor and have been able to receive messages but not send. I have stumbled upon a few related threads that have recommended adding the port number to the outgoing server configuration. This hasn't help and after messing around with various settings( as well as restoring them back), I haven't found a way to send.

I am using:Ubuntu 9.10 64, mail2world, settings are: 

pop3.mail2world.com & imap4.mail2world.com

Receiving is set to password
Sending is set to Login

Any help or suggestions would be appreciated

Ex

Why are you not using smtp.mail2world.com ?

---

### Post by exkend on 2009-11-30
I am very sorry but I meant to write: smtp.mail2world.com. not imap4...

By the way I am also trying to access emails via mail2world on my LG KC550 and am having the exact same problem. 

Thanks for the replies

Ex

---

### Post by dcstar on 2009-12-02
> **exkend said:**
> I am very sorry but I meant to write: smtp.mail2world.com. not imap4...

By the way I am also trying to access emails via mail2world on my LG KC550 and am having the exact same problem. 


Then you need to get the **exact** instructions from the mail provider on how to set things up.

---

