---
title: "How do I add repositories?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by brawd on 2010-04-03
Hi there,

I've just installed 10.04, and by not paying attention during the installation I also wiped 8.04, so I might be on borrowed time until it crashes. However I might as well bash on with what I've got.

It seems that 10.04 hasn't got the repositories that 8.04 had, and I need at least sun java 6 jre. I can't find it in the repos on offer to me, so I'll need to find it and install it. I also need some files or dependencies for gnucash.

Anyone got any ideas on how I load and configure these repos please.

regards,

brawd

---

### Post by clive littlewood on 2010-04-03
Add the medibuntu repo and then install ubuntu-restricted-extras.

That should get you going.

Also make sure the correct boxes are ticked in your software sources.

Clive

---

### Post by brawd on 2010-04-03
Thank you Clive

---

### Post by heepie on 2010-04-03
Java 6 have been removed from the repos since 10.04 and it's using the open source version openjdk. If you want to install java you gonna have to install it manually.

Have a look at:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by howefield on 2010-04-03
> **heepie said:**
> If you want to install java you gonna have to install it manually.

No, manual installation isn't required. The Sun java packages have been moved to the "partner" repository. Enable via Synaptic Package Manager > Settings > Repositories > Other Software.

---

