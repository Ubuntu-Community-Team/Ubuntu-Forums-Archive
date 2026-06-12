---
title: "packet modification"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by oarecare on 2007-12-20
need to do the following on a computer designed as router, running ubuntu 7.10:

process all packages going to a certain url:port by:
-decrypting the entire package
-checking for certain keywords (stored in db)
-if found, logging to mysql database, replacing them and reencrypting the package
-sending the new package to the recipient

same goes for packages coming from a certain url:port

Any suggestions on how to achieve this? Can it be done with apache and iptables?

---

### Post by kidders on 2007-12-22
Hi there,

I'm not sure it's easy to make arbitrary modifications to network packets, but even if it is, your use of the term "url" suggests you're talking about HTTP. HTTP over SSL encrypts data at the protocol level, so there would be no way to decrypt it at the packet level ... or are you talking about HTTP over IPSec, perhaps?

Then again, maybe you're not thinking of doing this with HTTP at all! Could you describe what you're trying to achieve?

---

### Post by oarecare on 2007-12-22
actually it is a chat program (yahoo-like), which sends the packages in encrypted xml format (<message id=889 value='regadagtrt!@$#fdafgfasda'>. I managed to decrypt it using apache (entering the entire package in a textarea and receiving the decoded/modified/reencoded package in another textarea.
What i am trying to achieve:
-let the program believe it is connecting to the server ip : port
-process the  packages both ways (using different scripts for incoming/outgoing packages)

the process would go like this:
server sends a package- the router (ubuntu) receives it, decodes it, modifies it, re-encodes it, sends it to the recipient WITHOUT CHANGING ANY HEADERS (completely transparent)

---

### Post by kidders on 2007-12-22
Interesting. What protocols is this built on?

Chances are what people think of as a router won't be able to do this sort of thing, because they operate at the packet level. My advice is to think "proxy", not "router". Depending on what protocols you've built your chat app on top of, you may or may not have to write your own.

---

### Post by oarecare on 2007-12-22
i really do not know. Using wireshark (a protocol analyser) the chat is reported as tcp; reversing the chat app showed me the encryption algo used. Was also able to replicate the encryption/decryption mechanism using apache.

My question is the following: can iptables be configured to use a certain app for modifying the packages? Can you provide me with an example on how to achieve this?

thanks in advance

---

### Post by kidders on 2007-12-22
The reason I'm interested in the detail of your protocol stack is that unless you've specifically written the app to operate & encrypt at the packet level, a router is simply the wrong tool for the job, to say nothing of the security issues involved. There would be tremendous disadvantages to the approach, so there would be no reason to write your app that way, unless it was a proof of concept for a university assignment, or something like that.

It seems far more likely that a proxy is what you need ... ie something that operates on top of TCP, not underneath it. Typically proxies do the exact opposite of what you want (ie tweak request/response headers, while leaving the payload intact), but there is no reason why you couldn't make one that breaks the "rules".

I still don't know for sure, but I'd say the answer to your question about whether iptables alone can be used is no. Unless you know it can (eg because you wrote it that way on purpose), it probably can't.

---

