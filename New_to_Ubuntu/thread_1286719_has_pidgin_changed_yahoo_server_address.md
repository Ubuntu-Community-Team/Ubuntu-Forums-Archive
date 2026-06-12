---
title: "has pidgin changed yahoo server address"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by nnamdi on 2009-10-09
i woke up this morning only to find out that i cant login into my yahoo acc. i.e yahoo chat on pidgin but try i on widows xp yahoo messenger and i could anyone having the same issue

---

### Post by comsparks on 2009-10-09
I had the same thing the other day and under Pager Server I put scsa.msg.yahoo.com and everything up and running again.

---

### Post by falconindy on 2009-10-09
Chances are you just need to upgrade to the latest release (2.6.1). You'll need to add a repository and get it from there. You can install it with the following commands:
```
echo "deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
gpg --recv-keys 7FB8BEE0A1F196A8
gpg --export --armor 7FB8BEE0A1F196A8 | sudo apt-key add -
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by alexcckll on 2009-10-09
Same issue here... I had to go to Yahoo's website and fill in two memorable questions.

WHAT THE HELL IS GOING ON????  I would just like to USE Pidgin the way it comes on Hardy to connect to Yahoo!

---

### Post by advocate 21 on 2009-10-09
did you subtract the "@yahoo.com" part? that worked for me.

---

### Post by LowSky on 2009-10-09
> **alexcckll said:**
> WHAT THE HELL IS GOING ON????  I would just like to USE Pidgin the way it comes on Hardy to connect to Yahoo!

That would be great, but Yahoo sets the rules, NOT PIDGIN. Pidgin tries to keep things running smoothly but in order to do that it needs updates. so for that matter you can blame Ubuntu

---

### Post by Thelasko on 2009-10-09
I have Pidgin 2.6.1 on my Hardy system and am experiencing the same problem.

---

### Post by alexcckll on 2009-10-09
> **LowSky said:**
> That would be great, but Yahoo sets the rules, NOT PIDGIN. Pidgin tries to keep things running smoothly but in order to do that it needs updates. so for that matter you can blame Ubuntu
Would there be any point in Canonical talking with Yahoo - and maybe getting an official Linux client library?

---

### Post by LowSky on 2009-10-14
> **alexcckll said:**
> Would there be any point in Canonical talking with Yahoo - and maybe getting an official Linux client library?

Canonical has nothing to do with Pidgin. Yahoo wants people to use their approved program. All you need to do is keep your software upgraded. Even if you don't want to upgrade the OS upgrading pidgin by itself is not that hard

[http://www.getdeb.net/release.php?id=4743](http://www.getdeb.net/release.php?id=4743)

If you want to complain to someone, complain to Yahoo!

---

