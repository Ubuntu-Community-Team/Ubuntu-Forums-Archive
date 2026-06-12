---
title: "Prism webapp closes despite being docked with Alltray"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by karl-arthur on 2010-08-29
Hi,

I have a Prism app (Google Tasks) set to run at startup in Lucid, and use Alltray to automatically dock it to the system tray. The command I use is:

alltray -st -na -g 300x400+1200 "prism" -override "/~/.webapps/tasks@prism.app/override.ini" -webapp [email]tasks@prism.app[/email]

The app starts correctly, however when I open it and then close it again, it exits completely instead of going back to the tray, as it should. If I click the tray icon instead of the close button, it minimizes back to the tray. 

I've tried adding and removing -nm from the command, which doesn't seem to make any difference. I should also mention that an identical setup (cut and pasted) works perfectly on a UNR installation I have on a different partition. 

Any ideas on how to solve this?

---

