---
title: "can i configure Ubuntu server as a root dns server ?"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by Andrea_Gaffiero on 2015-02-05
Hi im configuring my thesis testbed and I can't find anything on how to configure a root dns server using bind. Is it possible to configure a root dns server on Ubuntu? and if yes how do I do so?,

thanks.

---

### Post by newbie-user on 2015-02-05
You should probably talk to [IANA]("https://www.iana.org/domains/root") first...

---

### Post by lisati on 2015-02-05
Yes, Ubunutu can be used to provide DNS services.

Some clarification on what you are hoping to achieve might be useful: as newbie-user rightly points out, what some of us understand by the term "root dns server" is something that IANA normally deals with.

---

### Post by Andrea_Gaffiero on 2015-02-06
basically im configuring a private network in which no public communication will take place. I need to configure an authoritative dns server for the root domain, an authoritative dns server for the ".com" domain, and an authoritative dns server for the "mynetwork.com" domain, a caching dns server and a desktop client. The problem I've encountered is configuring the root authoritative dns server and I can't find any tutorials/guidelines on how to configure it. Any other suggestions besides IANA? I don't think i need to contact IANA in such a scenario due to the fact that the root dns server will operate within a private network.

thanks for the previous replies.

---

