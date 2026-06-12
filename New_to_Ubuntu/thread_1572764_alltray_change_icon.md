---
title: "alltray change icon"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by ssdt on 2010-09-11
Is it possible at all to change the icon that is shown at the tray for an alltray application to change? I see a regular alltray icon but I want to customize that? Is there any way?

---

### Post by kerry_s on 2010-09-11
read the manual

man alltray  (long version)
or
alltray --help  (short version)

---

### Post by ssdt on 2010-09-12
I read the manual but it does not help. There is not way i can use -i for icon

---

### Post by anibalismo on 2012-03-27
Hi! i know it is an old post, but...

I was trying to do [this (gtask+alltray trick) ]("http://namsisi.wordpress.com/2009/02/22/gmail-tasks-in-your-ubuntu-system-tray/")and wanted to change the prism icon for the gtask icon, so I modified the ¨program¨ property to this:
```
alltray -st -na -g 300x724+980 -i /home/anibalismo/.prism/gtask.png xulrunner-1.9 /usr/share/prism/application.ini -webapp tasks@prism.app
```notice I used the full image address.

Hope this help!:popcorn:

---

