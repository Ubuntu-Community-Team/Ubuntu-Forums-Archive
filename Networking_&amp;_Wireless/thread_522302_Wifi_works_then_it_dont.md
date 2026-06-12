---
title: "Wifi works then it dont?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by redline135 on 2007-08-10
Now Im sure that this part of the forum is burnt out on wifi questions but I will ask anyway. 

I have a low end notebook from gateway (ya i know) model MX3231. The 1 thing that never got detected was the video ( always had to use the vesa driver until i found Openchrome). But just recently with the new version of Ubuntu 7.04 my wifi was not being found. The previous versions of Ubuntu worked great, no problems with any networking device. Now it will only find my NIC and not my wifi. I have also tried the Alpha of 7.10 and get the same results, no wifi. I dont really want to stay with version 6.10 but Im guessing I will have to unless I can find a work around or if anyone knows what the problem is, or can point me in the right direction I will go there.... 

Thanks in advance .... 



ReDLiNe-----

---

### Post by clearzen on 2007-10-08
Okay, the driver for your internal wireless card is in the blacklist file. the driver is at the end of the /etc/modprobe.d/blacklist file.

---

### Post by clearzen on 2007-10-08
heh, forgot to tell you how to fix it. Either delete the line rtl-8185 or it maybe rtl-8187 or rtl-818x. In any case it will be a rtl driver. You can comment out the line with a # at the start of the line. Hope that helps.

---

