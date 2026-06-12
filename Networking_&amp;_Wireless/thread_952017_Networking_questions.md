---
title: "Networking questions"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by fireoptic on 2008-10-18
Hello, I'm relatively new to Linux in general but I'm getting the hang of it.

I have some questions about file sharing that I just cant seem to find the answers to. I would like to be able to share files on my network across an as yet undetermined  number of computers running either microshaft or Linux. I would also like to be able to access these files anywhere that has a connection and a computer. Is samba for me or should I look into something else?

Any help would be much appreciated.

---

### Post by pdwerryhouse on 2008-10-18
When you say "anywhere", do you mean you want to be able to access the files from outside your network (ie, across the internet)?

In that case, Samba is probably not what you're looking for.

Samba is a good choice for accessing within your own network, but if you want to distribute files across the internet, I'd be looking at using a webserver (eg, Apache).

---

### Post by fireoptic on 2008-10-18
Thanks for the input!

---

