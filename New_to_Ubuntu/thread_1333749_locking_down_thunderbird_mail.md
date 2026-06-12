---
title: "locking down thunderbird mail"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by mjp29 on 2009-11-21
I don't want the box to continue to boot and allow folks to use my firefox browser and such.  I don't want them to access my email.

I took steps to password protect my ingoing/outgoing mail in thunderbird mail; however, I've noticed that even if a user doesn't know my password they can proceed to view my emails i received or sent yesterday.

how do i lock down *only* thunderbird mail?

---

### Post by mt1234 on 2009-11-21
Do you have a separate user login account setup for the other users that does not have administrator priviledges?

---

### Post by peculiar penguin on 2009-11-21
> I don't want the box to continue to boot and allow folks to use my firefox browser and such. I don't want them to access my email.Password protect your account? It should have been set up that way by default after installing.

> I took steps to password protect my ingoing/outgoing mail in thunderbird mail; however, I've noticed that even if a user doesn't know my password they can proceed to view my emails i received or sent yesterday.If you let other people use your account, they could always just go into the hidden directory where your mail is stored in plain text and read it with a text editor or something... unless you break out encryption, which isn't necessarily "Absolute Beginner Talk".

> how do i lock down *only* thunderbird mail?     Different question now? :confused:
It can be done, but unless you're going for security by obscurity you'd need to create an additional, encrypted file system you can mount/dismount on demand (e.g. an encrypted partition using LUKS/dm-crypt, or a container file with Truecrypt,...) and then move your Thunderbird profile inside. Decidedly not "Absolute Beginner Talk".

---

