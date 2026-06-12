---
title: "want to run a terminal command at startup."
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by laeeq2 on 2013-10-15
hello..!


i want to run this command at startup which starts my WIFI in ubuntu 12.04.

[B][COLOR=#8b4513]sudo modprobe -rf hp_wmi

[/COLOR][/B]any solution...?


Thanks...

---

### Post by drmrgd on 2013-10-15
Do you want this to run at boot or when the desktop loads?  If the former, then you might check out upstart:

[https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)[URL="http://upstart.ubuntu.com/"]
http://upstart.ubuntu.com/[/URL]

If you want the latter, then adding and entry to "Startup Applications" would be what you want.  Check out these detailed instructions here:

[http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)

---

