---
title: "yahoo and pidgin"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by joshuapbell on 2009-01-05
Does anyone know why pidgin seems to never want to connect to yahoo messenger.


I have pidgin 2.5.2 on Ubuntu 8.10 and it doesn't connect for a long time, then eventually for no reason at all it will connect to yahoo. All the other protocols seem to work fine. Am I the only one with this problem or are there others, is it an issue with Ubuntu, pidgin or yahoo??? anyone know?


Thanks for any ideas

---

### Post by adobrakic on 2009-01-05
2.5.3a came out, you can try that one to see if it helps any

---

### Post by SunnyRabbiera on 2009-01-05
Yahoo has always been ellusive with pidgin it seems, I suggest you try empathy, it might be better as empathy shows a lot of promise.
Also try kopete

---

### Post by Antonio Lo Nardo on 2009-01-06
> **joshuapbell said:**
> 
I have pidgin 2.5.2 on Ubuntu 8.10 and it doesn't connect for a 
Thanks for any ideas

I have Pidgin 2.5.2 and it works fine with Yahoo.
Try to check the account configuration.

---

### Post by rolnics on 2009-01-06
I never seem to have a problem with it, it's always hotmail that's the problematic one for me.

I would also suggest checking your account setup

---

### Post by HotShotDJ on 2009-01-06
Using Pidgin 2.5.2 connected to Yahoo right this moment.  No issues at all.  Check your settings.

---

### Post by Ashrael on 2009-01-09
Hi all!

I had the same problem, so decided to install 2.5.3 form source...had to install a bunch of dev packages, and then: still the same error! Since it was a resolving error, I decided to change the server scs.msg.yahoo.com to it's ip adress  66.163.181.167....

No connection probs after that!

HTH!






:popcorn:

---

### Post by khc on 2009-01-09
> **Ashrael said:**
> Hi all!

I had the same problem, so decided to install 2.5.3 form source...had to install a bunch of dev packages, and then: still the same error! Since it was a resolving error, I decided to change the server scs.msg.yahoo.com to it's ip adress  66.163.181.167....

No connection probs after that!

HTH!






:popcorn:

If it's a resolve problem, then it's probably because you are using a crappy router as upstream dns. Configure your router to send the upstream dns servers directly to you instead of being the dns server should fix that.

The issue is that the dns response is bigger than the largest size allowed by UDP (which dns typically uses) and when that happens, the resolver is supposed to fallback to TCP, but on many routers this is not done correctly.

---

