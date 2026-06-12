---
title: "[SOLVED] Need a download manager"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-12-16
Hi everyone, I need a download manager for ubuntu similar to [internet download manager](http://www.internetdownloadmanager.com/).

In particular I need one with these features.


[LIST]
[*]Scheduled downloading. It must be able to start all downloads at a certain time, then stop them again at another time.
[*]It should be able to take over download links from firefox. Not absolutely needed but would be very helpful.
[*]Should be able to start at logon and sit in the tray, so it is running at all times.
[/LIST]
If anyone knows a program that has these features (especially scheduled downloading) please let me know, I would very much appreciate it.

Thanks,

Talsemgeest.

---

### Post by hyper_ch on 2008-12-16
DownThemAll extension for Firefox?

D4X?

---

### Post by Bachstelze on 2008-12-16
Aria will do what you want (and much more). It's GTK 1.2, however, so it's not very pretty, but as I said, it will get the job done.

```
sudo apt-get install aria
```

(You can integrate it into Firefox with the FlashGet extension.)

---

### Post by Archmage on 2008-12-16
Wget

---

### Post by Bachstelze on 2008-12-16
> **Archmage said:**
> Wget

If you fancy cron and shell scripting. May I remind you we're in Absolute Beginner Talk?

---

### Post by Perfect Storm on 2008-12-16
gwget

---

### Post by Bachstelze on 2008-12-16
> **Artificial Intelligence said:**
> gwget

Can gwget start and stop downloads at a given time? It's been a while since I tried it, but I remember it didn't have many features (which is why I usually recommend Aria).

---

### Post by alienexplorers on 2008-12-16
I don't beleive DownThemAll allows scheduling of download times.

---

### Post by Perfect Storm on 2008-12-16
I think it can now. It have resume, stop buttons. And if you use epiphany browser you can install its extenstion so it become a part of epiphany browser.

---

### Post by talsemgeest on 2008-12-16
> **hyper_ch said:**
> DownThemAll extension for Firefox?

D4X?

I don't think down them all supports scheduled downloads, and downloader for x doesn't automatically take over downloads from firefox. However, I will leave that as my backup plan.

> **Artificial Intelligence said:**
> gwget

Thanks, I'll give it a try.

> **HymnToLife said:**
> Aria will do what you want (and much more). It's GTK 1.2, however, so it's not very pretty, but as I said, it will get the job done.

```
sudo apt-get install aria
```(You can integrate it into Firefox with the FlashGet extension.)Thanks, I think this sounds about perfect. However, I can't figure out how to schedule the downloads (I cant find an option anywhere in the program). Also, is there an option for adding the downloads as stopped?

EDIT: Never mind, I found the scheduler. Thanks again HymnToLife.

---

### Post by kpkeerthi on 2008-12-16
D4x integrates with firefox via [flashgot]("https://addons.mozilla.org/en-US/firefox/addon/220")

---

### Post by talsemgeest on 2008-12-16
Also, does aria start at system startup? If it doesn't, is there any way to make it run in the background, preferably in the system tray?

---

### Post by Bachstelze on 2008-12-16
> **talsemgeest said:**
> Also, does aria start at system startup? If it doesn't, is there any way to make it run in the background, preferably in the system tray?

I think Gnome lets you specify a list of programs you want to be run at startup in its session manager. Aria doesn't have a "run in systray" feature in itself, but you should be able to achieve that with AllTray.

---

### Post by talsemgeest on 2008-12-16
> **HymnToLife said:**
> I think Gnome lets you specify a list of programs you want to be run at startup in its session manager. Aria doesn't have a "run in systray" feature in itself, but you should be able to achieve that with AllTray.
Thank you very much once again, you have helped me out immeasurably.

Problem solved.

---

