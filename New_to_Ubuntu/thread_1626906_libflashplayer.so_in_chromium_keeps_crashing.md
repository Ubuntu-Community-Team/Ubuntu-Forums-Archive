---
title: "libflashplayer.so in chromium keeps crashing"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by locodog on 2010-11-20
Almost everyday i keep getting this message from Chromium:
/usr/lib/flashplugin-installer/libflashplayer.so crashed. It's not real problem, because my browser keeps working, but it's really annoying seeing that message everyday. Everything on my Chromium 7.0.517.44 Ubuntu 10.04 is updated, and I don't know why this is happening. Really i don't care WHY it's happening i just want to fix it! Can somebody tell me how?

---

### Post by taseedorf on 2010-11-20
You can check the logs to see the real problem, but flash has always had problems in Linux.  Does flash crash in Firefox, too?  If it doesn't, it's probably a conflict within Chromium so make sure you upgrade to the latest version.

---

### Post by locodog on 2010-11-20
How to check logs? I'm not using firefox, i have it installed, but i'm always using chromium... And i'm always up-to-date, i'm updating everything, everyday.

---

### Post by branscombe_richmond on 2010-11-27
as usual noone will help with this.  i am having the same issue here and cant find an answer.



bumping this thread.  all with butthurt need not reply, this is a real issue.

---

### Post by sandyd on 2010-11-27
See attached image. (starting from top to bottom circles).

In the last circle, note the location of the plugin.
if you want to disable it, press disable.

thats the flash plugin btw.

---

### Post by locodog on 2010-11-28
Am I missing something... I don't see why would I disable flash (altrough that would definetly solve the problem, but would my browser than show flash content)?

---

### Post by sandyd on 2010-11-28
> **locodog said:**
> Am I missing something... I don't see why would I disable flash (altrough that would definetly solve the problem, but would my browser than show flash content)?

correction: your going to be disabling the inbuilt chromium flash and enabling the external one.

---

### Post by locodog on 2010-11-28
Ok. I did that... now i just need to wait enough time to see if it works :)

---

### Post by davsousa on 2010-12-07
chromium does not have an internal flash player like windows CHROME, its uses the flash plugin as default.

Disabling it, disables flash at all.

still not solved, flash crashing like hell in chromium =(
seems normal in firefox

---

### Post by wojox on 2010-12-07
Try copying it into Chromium

[Howto enable flash support for chromium browser]("http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html")

---

### Post by ibizatunes on 2010-12-07
delete your chrome folder in your home directory
/home/username/.local/chrome
i had the same issue, worked fine after that for me

---

