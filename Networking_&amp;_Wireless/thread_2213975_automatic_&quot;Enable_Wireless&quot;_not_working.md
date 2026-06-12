---
title: "automatic &quot;Enable Wireless&quot; not working"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by marcw on 2014-03-29
I've installed 12.04 on a couple other laptops without issue.  But on my newly aquired Elitebook I've run into an issue that a couple hours of searching hasn't helped me resolve.

laptop = HP Elitebook 6930p
wireless card = Intel 5300
interface = wlan0

12.04 installed fine and works well.  But I have to manually choose "Enable Wireless" from the network menu after each restart.  Once I do that my default network is discovered immediately and everything works well after that.  

How do I get "Enable Wireless" to be automatically selected from the network menu after a restart like it is on my other laptops?

---

### Post by marcw on 2014-03-30
While I didn't determine root cause of this I did find a workaround.  According to rfkill, it seems my wlan0 is being soft blocked.  I don't know why.  But by inserting "rfkill unblock all"  in my rc.local file the radio turns on, my wireless connections are established, and everything works.

---

