---
title: "Secure Googlemail connections via Evolution"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2010-06-09
Hi,
   This is not a problem so much as a couple of questions to increase my understanding and determine if I have a problem.

I have 2 Googlemail (IMAP) accounts which I operate via Evolution. I have configured Evolution to make secure connections (SSL) to both email accounts. My questions are:

1. Can Evolution make simultaneous **secure** connections to both Googlemail accounts via the same ports?

As far as I know, connection for incoming mail is made only via port 993, outgoing is port 465 or 587.

2. If this is a stupid question then sorry for my ignorance but can a port handle more than one connection securely? 

I read somewhere that email clients that don't allow you to specify the port for connection (like Evolution) can silently fall back to a non-secure connection when they can't establish a secure connection. 

So you would never know if this happened and it may happen all the time if you try to operate 2 Googlemail accounts simultaneously via the same port, if the port cannot handle more than one connection securely.

Thanks in advance

---

### Post by Noo 2 Ubuntoo on 2010-06-13
Ok, for anyone interested I found the answer in a Googlemail forum and the answer is yes, multiple secure connections can be established via the same port. 

Evolution silently falling back to a non secure connection if it fails to connect securely is a potential problem, depending on how much you want a secure connection. 

An alternative that  simply won't connect if it can't connect securely is Thunderbird, because you specify the connection port in the set up procedure for Thunderbird.

---

