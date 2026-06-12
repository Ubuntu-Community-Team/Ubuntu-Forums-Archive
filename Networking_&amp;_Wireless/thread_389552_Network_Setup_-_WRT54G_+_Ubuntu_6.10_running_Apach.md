---
title: "Network Setup - WRT54G + Ubuntu 6.10 running Apache: will this work?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by archer007 on 2007-03-20
Hey guys, I wanted to run an idea for a network that I am going to make past you, and get advice/comments/suggestions, as I am not sure how to do it all.

Ok, so I want an unencrypted wireless network, that, when people connect to it and use their browser, they are redirected to a list of files that are hosted by a server on the network, and can then download those files.

So..

I need a server, which I have: my old desktop. I plan to get it running Ubuntu 6.10 (currently SuSe 10.1) with Apache server and some captive portal software.

A wireless router. A Linksys WRT54G would work, I think. It would not be connected to the Internet.


Problems:

- I can't find captive portal software for linux in binary form. EDIT: nvm I should be able to find it in some package repository....
- How will I make http requests redirect to the server? Change some settings in the Linksys?

---

### Post by Floppyjoe on 2007-03-21
You can forward port 80 to your server. That is the Http port.

---

### Post by archer007 on 2007-03-31
How?

---

