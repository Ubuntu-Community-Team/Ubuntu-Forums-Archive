---
title: "Keeping SSH secure when on untrusted networks?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by talz13 on 2008-07-21
I'm going to be traveling overseas next month, and plan to be connecting to my server at home via SSH and/or winSCP.  Since I don't really trust any of the networks I'm going to be using, what is the best way to protect my SSH?  Is it just good enough by itself?  Should I make a keyfile to login with?

What about if I have to use (ugh!) an internet cafe PC instead of my laptop?  Then I wouldn't trust the connection OR the computer!  I mostly just want to upload my photos from my laptop so that I don't lose everything in the event of a lost/stolen/dead laptop.

---

### Post by sp0nge on 2008-07-21
I am new to using SSh myself, but from what I understand, this should provide you with good security. If you don't trust the machine you're using, I would just not do it, but on your laptop, SSh is just fine as far as I understand.

---

### Post by tava0002 on 2008-07-21
If you'll be on your personal laptop connecting to a home server the encryption is between those two machines.  If anything interferes with that connection by decrypting etc..., it would be considered a man in the middle attack.

---

### Post by talz13 on 2008-07-21
> **tava0002 said:**
> If you'll be on your personal laptop connecting to a home server the encryption is between those two machines.  If anything interferes with that connection by decrypting etc..., it would be considered a man in the middle attack.

And, if I've connected before and gotten the valid fingerprint, I should get one of those little warning messages saying that the fingerprint has changed?

---

### Post by Endwin on 2008-07-21
Yup in fact if it is different it will not let you connect if it has seen that combo before. One word of caution connect to it at least once how you will through the net. That way you have the fingerprint of the server from the outside. I usually access my servers from the internal network not over the net, so if I am on a trip then it will be a diffrent fingerprint for the outside.

---

