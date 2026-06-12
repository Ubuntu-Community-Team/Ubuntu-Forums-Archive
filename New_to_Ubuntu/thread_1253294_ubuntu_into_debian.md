---
title: "ubuntu into debian"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by cmannnn on 2009-08-29
please help me my ubuntu splash screen dosent say ubuntu it says debian(most likely spelled wrong) i know thats the back bone of ubuntu but my screen is  b/w and web pages dont show any thing plz help me get ubuntu back

---

### Post by cariboo on 2009-08-29
Do you have Debian repositories in you /etc/apt/sources.list? You can install startupmanager to change the startup screen. Startupmanager is in the repositories. As for your firefox problem, you may have a corrupted profile. Open a terminal and type:

```
firefox -ProfileManager
```

create a new profile to see if that makes any difference.

---

### Post by 3rdalbum on 2009-08-29
Or you might have the "usplash-theme-debian" package installed. Remove it and reinstall the "usplash-theme-ubuntu" package to get back your Ubuntu splash. Your other problems might be unrelated (or might be the result of you putting Debian repositories into your sources.list).

---

### Post by cmannnn on 2009-08-30
thanks ill try

---

