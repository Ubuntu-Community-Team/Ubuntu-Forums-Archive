---
title: "Adoble flash, etc"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by arvadawest on 2010-09-16
Hi,

I am a newbie.  I am running 8.04 LTS.  I've noticed many sites I visit say I need a newer version of adobe flash or that it's crashed.  I assume my system has not been receiving updates... well, I'm just not sure.  How do I get received or install the latest adobe updates so I can view items on websites?   Thank you. :)  -aw

---

### Post by Rubi1200 on 2010-09-16
For problems with Flash:
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

### Post by sikander3786 on 2010-09-16
Have there never been any updates? Go to Software Sources under System > Administration menu. Go to the Updates tab and make sure there is a tick mark on Important Security Update, Recommended Updates and Unsupported Updates. Then from Terminal,

```

sudo apt-get update

```

```

sudo apt-get upgrade

```

That might solve the issue. Also there is a nice link posted by Rubi above. Hope it helps you.

---

