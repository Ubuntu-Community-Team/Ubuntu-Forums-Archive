---
title: "Updating Thunderbird"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by daniell59 on 2010-04-14
I want to update Thunderbird 2.0 to 3. I downloaded it. Now how do I install it? I am using Ubuntu 9.10.

Thanks

---

### Post by undecim on 2010-04-14
According to what I have, Thunderbird in the repositories is already version 3.
```
$ aptitude show thunderbird | grep Version
Version: 3.0.5~hg20100409r4809+nobinonly-0ubuntu1~umd1~karmic
```

So all you have to do is install it from the Software Center.

---

### Post by daniell59 on 2010-04-14
> **undecim said:**
> According to what I have, Thunderbird in the repositories is already version 3.
```
$ aptitude show thunderbird | grep Version
Version: 3.0.5~hg20100409r4809+nobinonly-0ubuntu1~umd1~karmic
```

So all you have to do is install it from the Software Center.

I checked and only see version 2.0.
I downloaded it then extracted it. At this point I am lost.

Thanks

---

### Post by empty_spaces on 2010-04-14
Instead of downloading it, I would recommend installing it by adding the appropriate PPA/Repos.

See this link:
[http://www.ubuntugeek.com/how-to-install-thunderbird-3-in-ubuntu-9-109-048-108-04.html](http://www.ubuntugeek.com/how-to-install-thunderbird-3-in-ubuntu-9-109-048-108-04.html)

Also, if you are on 64bit and use the Lightning/Google Calendar extensions, these will not work in Thunderbird 3. You will have to manually download updated versions  and install in Thunderbird 3.

---

