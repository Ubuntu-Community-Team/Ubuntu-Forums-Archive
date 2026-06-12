---
title: "Can't open links in Evolution, PDF files, etc."
date: 2010-05-28
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-28
I had Google Chromium installed, but I uninstalled it awhile ago and now I can't open links in my email or PDF files. It keeps saying that a Chromium file can not be found. Any help with this? I am not using Firefox.

---

### Post by vandorjw on 2010-05-28
How did you install chromium?

is it in the repositories?
if it is try sudo apt-get purge "chromium"
(This removes the configuration files and any such personalizations you may have made)

If you don't have firefox, and you removed chromium, it makes sense you cannot open links...unless you have something else like galion installed.

---

### Post by lovinglinux on 2010-05-28
> **cc7gir said:**
> if it is try sudo apt-get purge "chromium"

The correct command would be:

```
sudo apt-get purge chromium-browser
```

The package chromium is a game.

Anyway, that probably won't fix the issue.

The OP needs to change the browser in the Preferred Applications.

---

### Post by UnknownFear on 2010-05-29
> **lovinglinux said:**
> 
The OP needs to change the browser in the Preferred Applications.

That worked! Thank you SO much!!

---

