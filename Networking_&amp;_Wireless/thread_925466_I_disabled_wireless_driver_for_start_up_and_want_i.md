---
title: "I disabled wireless driver for start up and want it back"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by deadlockedgamer on 2008-09-20
I need help. I was having issues with wireless connection in ubuntu intrepid. So I disabled it on start up using instructions I found and tried to use nds wrapper. However it gives an a chrash report every time I click configure wireless. So I want to re enable the default driver at start up using the terminal. What cammand would I use?

---

### Post by ladr0n on 2008-09-20
That depends on how you disabled it.  If you added it to your /etc/modprobe.d/blacklist file, you need to open that file (gksu gedit /etc/modprobe.d/blacklist) and comment out the line where you blacklist your wireless card driver.  If you disabled it through some other means, re-enabling it would be different though.  Can you remember how you disabled it, exactly?

---

### Post by deadlockedgamer on 2008-09-21
I probably put it on the blacklist. All I no is I typed it in on the terminal and the person who said how to do it also said it only removes it from start up but does not delete it.

---

