---
title: "how do i use clamav to scan thunderbird"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-09
how do i use clamav to scan thunderbird incoming and outgoing mail? I heard that thunderbird had an addon but can not find it. Also heard that the add on could be out dated. also heard that their might be something in synaptic but again can not find it. I'm tired of the hear say and come to you the experts to find out how to do this.

---

### Post by marl30 on 2011-01-09
> **lance bermudez said:**
> how do i use clamav to scan thunderbird incoming and outgoing mail? I heard that thunderbird had an addon but can not find it. Also heard that the add on could be out dated. also heard that their might be something in synaptic but again can not find it. I'm tired of the hear say and come to you the experts to find out how to do this.
Possibly, this what you are looking for in Synaptic: Mailsanner -> MailScanner is a email gateway virus-scanner and spam and
 phishing-detector. It uses Exim, sendmail or postfix as its basis,
and supports clamav and some commercial virus scanning engines to do
the actual virus scanning. For spam dectection MailScanner uses
spamassassin.

The action taken on virus, spam or phishing mails can be configured
with a flexible ruleset based on sender, receiver, scoring etc.

Virus checking is disabled and spam checking is enabled by default.

---

