---
title: "Why does RealPlayer have to install the postfix mail server?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by abyssius on 2009-02-23
I recently encountered the error message:

```
postfix: fatal: open /etc/postfix/main.cf: No such file or directory
```

I didn't need postfix, so I uninstalled it. During the removal process, it also removed realplay, so I could no longer view realplayer videos. I re-installed RealPlayer 11 from the .deb file available on their site, and as part of the process RealPlayer re-installed postfix. I now have the same error message again. I'm wondering why RealPlayer installs a mail server on my computer - and how is RealPlayer utilising it?

---

### Post by sydbat on 2009-02-23
I've always viewed it as spyware. You should be able to use other media players that are FAR superior found in the repos.

---

### Post by brian_p on 2009-02-23
> **abyssius said:**
> 

I'm wondering why RealPlayer installs a mail server on my computer - and how is RealPlayer utilising it?

RealPlayer11GOLD.deb depends on lsb which depends on lsb-core which depends on mail-transport-agent.

You would have to ask real.com why they do that. My .deb of realplayer does not have the dependency on lsb.

---

