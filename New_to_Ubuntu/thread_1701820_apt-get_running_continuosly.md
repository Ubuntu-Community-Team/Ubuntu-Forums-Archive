---
title: "apt-get running continuosly"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Dagorath on 2011-03-07
Every time I have run the top command in the past 24 hours it has reported that apt-get is running at 95% to 100% CPU.  Under the time+ column in top it reports 851:42:85.  It's running under the root account. I did not start apt-get so it seems the system started it for me for some reason.

Why is apt-get running and why has it stayed running for so long?

---

### Post by zenwalker on 2011-03-07
May be the update manager is running in background? Just disable this service. Also check if your network is slow or not and so is your repo server.

---

### Post by Dagorath on 2011-03-07
> **zenwalker said:**
> May be the update manager is running in background? Just disable this service. Also check if your network is slow or not and so is your repo server.

Yes, zenwalker,  the update manager is running.  I just did "man top" and discovered that pressing c while top is running causes top to show the command used to invoke the process.  Doing that shows me that apt-get was invoked with "apt-get -qq -y update".  The -qq parameter specifies quiet mode and the -y specifies answer yes to all questions.

So how do I disable the update service?

---

