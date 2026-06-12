---
title: "WPA Problems in Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by JCook21 on 2007-04-20
Hi everyone,

I'm wondering if anyone has managed to get WPA2 to work in Feisty.  I can't make it work using either Network Manager or wicd and I've had to reduce my routers security to WEP to get a connection working.  As far as I know wpa supplicant is installed.  It was working fine before I switched to Feisty and I've since tried a clean install to see if that would get it working, with no luck.  I have a Broadcom 4318 card with ndiswrapper drivers.

One other small question-what do I need to enter under sessions>startup programs to get the wicd applet in the notification area?  I've tried checking the wicd website but it seems to be down at the moment.

Thanks in advance for any help.

---

### Post by alex77 on 2007-04-23
"System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy

That works in edgy, i'm guessing it will be something similar in feisty..

---

### Post by p252 on 2007-04-23
WPA2 would not work for me with Feisty either. Have you tried just WPA? It works fine for me and is better encryption than WEP.

---

