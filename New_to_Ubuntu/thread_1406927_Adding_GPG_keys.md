---
title: "Adding GPG keys"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by A_M_S on 2010-02-14
To add a new repo after editing the sources.list we need to  add a GPG key. One way of doing it is:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5

The **apt-key adv** adds the GPG key locally right?

what is the purpose of the  "**--recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5**" ?

Is "**0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5**" the GPG key?


tnx.

---

### Post by cariboo on 2010-02-14
To answer your question, yes it is.

---

### Post by A_M_S on 2010-02-14
> **cariboo907 said:**
> To answer your question, yes it is.

Thank you for your reply.

But if  "0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5" is the GPG key, why do i have to connect to the keyserver.ubuntu.com?

Why not adding it simply do my system?

---

### Post by tom.swartz07 on 2010-02-14
> **A_M_S said:**
> Thank you for your reply.

But if  "0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5" is the GPG key, why do i have to connect to the keyserver.ubuntu.com?

Why not adding it simply do my system?

I may be incorrect in my interpretation of the idea, but it is my understanding that you need to verify the key with the remote server.

Just like having a real key, you need to locate the lock that it works in. Following the same reasoning, the key you have connects to the remote 'lock' repository and then verify that they are a pair.

---

### Post by A_M_S on 2010-02-15
> **tom.swartz07 said:**
> I may be incorrect in my interpretation of the idea, but it is my understanding that you need to verify the key with the remote server.

Just like having a real key, you need to locate the lock that it works in. Following the same reasoning, the key you have connects to the remote 'lock' repository and then verify that they are a pair.

I think you're right.
The following link has more info about apt-key.

[https://help.ubuntu.com/community/SecureApt]("https://help.ubuntu.com/community/SecureApt")

---

