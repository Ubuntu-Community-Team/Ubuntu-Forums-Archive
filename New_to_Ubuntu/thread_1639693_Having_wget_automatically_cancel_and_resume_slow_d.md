---
title: "Having wget automatically cancel and resume slow downloads"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by tg3793 on 2010-12-07
Good morning (or afternoon) everyone,

[COLOR="Purple"]**How would I get wget to stop itself and then automatically resume if the download speed drops below 30 Kbs ?**[/COLOR]


~~~~~~~~~~~~~~~~~~~~~~~~~~
**~** Background to problem **~**
~~~~~~~~~~~~~~~~~~~~~~~~~~

For some reason any download I start runs great for about ten to twenty seconds. It quickly builds up to 50Kbs to 90Kbs but then after aforementioned number of seconds it creeps down to 20Kbs and then finally under 5Kbs.

My current solution is to baby sit each download, canceling it and then resuming it with wget -c. This works great but it is very time consuming.


~~~~~~~~~~~~~
**~** Homework **~**
~~~~~~~~~~~~~
I've been crawling around the Internet for a few minutes at a time over the last month but today is the day I finally decided to hit this problem hard. I've been perusing Google, the wget man page and the forums for the last forty-five minutes trying to get the answer to this issue. And though I'm learning a lot but just not the answer to this question.

Thanks for any help you might be able to offer.

---

### Post by technocp on 2011-01-14
did you till now get any answer to this question

---

### Post by tg3793 on 2011-01-14
> **technocp said:**
> did you till now get any answer to this question

Nope. Just got a work-a-round so far. I started using aria2c instead and am using it with a list of urls in a text file. I still have to baby sit it.

If anyone comes up with a solution to this I would certainly appreciate it. Either my service provider is doing some bandwidth throttling that is triggered by long downloads or there is some sort of "build up" or "bandwidth leakage" (I don't know what to call it) that happens during long downloads.

In any case "baby sitting it" works and all I would need (I suppose) would be something that would kill my downloads every five minutes, pause for ten to twenty seconds, and then reintiate the downloads.

---

