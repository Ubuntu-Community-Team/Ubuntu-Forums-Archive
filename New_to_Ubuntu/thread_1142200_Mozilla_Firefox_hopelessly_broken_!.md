---
title: "Mozilla Firefox hopelessly broken !"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by ProgramErgoSum on 2009-04-29
Hi,
Lately, I had been getting message in Firefox that Java was not enabled even when the check-box had been checked and Java is installed. 

```

java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.4) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)

```


Not knowing what was wrong, I decided to re-install from Synaptic. Mistake !

Now, every time I start the browser, I get the message as seen in the first attachment (S1). The search box is also broken as seen in second attachment. Ctrl-T for new tab doesn't work either.

What else is to be installed/un-installed ?

I am at Intrepid. Upgrade to Jaunty is not an option currently.

---

### Post by llamabr on 2009-04-29
One quick fix is to mv your .mozilla directory, and let firefox create a new one:

```
mv .mozilla/ .mozilla.old/
```

and then start firefox

---

### Post by ProgramErgoSum on 2009-04-30
Thanks for the reply.

I forgot that FF was running in another workspace which I had forgotten to kill before restarting. I killed it, restarted FF and now everything is fine.

---

