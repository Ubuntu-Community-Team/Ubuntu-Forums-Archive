---
title: "youtube video will not play"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-04-06
im confused as to the cause of this i have restricted extras installed and i also have flash installed and enabled. anyone willing to help?

---

### Post by moffa on 2009-04-06
> **PatrickMoore said:**
> im confused as to the cause of this i have restricted extras installed and i also have flash installed and enabled. anyone willing to help?

Firstly, I would go to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and ensure Flash is configured properly.  If not just download it from the website (libflashplayer.so) and save it in /usr/lib/mozilla/plugins/.

---

### Post by PatrickMoore on 2009-04-06
i fixed it thank you

---

### Post by thesuperjman on 2009-04-06
i cant find the restricted extras for ubuntu

ps: here- [http://get.adobe.com/shockwave/-](http://get.adobe.com/shockwave/-) it says my platform is not supported. does this basically mean im ****** for web media?

---

### Post by Skorzen on 2009-04-06
> **thesuperjman said:**
> i cant find the restricted extras for ubuntu

That package is available in the repositories.
```
# apt-get install ubuntu-restricted-extras
```

---

