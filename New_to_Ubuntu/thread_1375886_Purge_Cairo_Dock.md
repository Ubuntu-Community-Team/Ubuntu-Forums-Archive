---
title: "Purge Cairo Dock"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-01-08
I had a little trouble installing cairo dock. I finally got it, but it has no themes at all other than the default, and when I try to add more they won't work. I would like to just completely purge cairo dock and start from the beginning. I tried 
[FONT=monospace]
[/FONT]sudo apt-get remove cairo-dock


It ran the processes and said that it was removed, but cairo dock still 
when I log in and is still under Applications>Accessories> Cairo Dock (no open GL). 
Is there a way to completely remove all traces of Cairo Dock?

---

### Post by steve-shinn on 2010-01-08
sudo apt-get --purge cairo-dock

---

### Post by Captainflowers91 on 2010-01-08
E: Invalid operation cairo-dock

Thats what I get when I try that terminal prompt

---

### Post by fabounet on 2010-01-08
the themes server is down at the moment, you have to launch it with 
cairo-dock -S [http://themes.vef.fr](http://themes.vef.fr)

or install the BZR version

---

### Post by Captainflowers91 on 2010-01-08
wow do I feel stupid. I thought I had screwed things up. Anyway, thanks. Any idea when it'll  be up again?

---

### Post by fabounet on 2010-01-09
around 2 weeks I hope.

---

