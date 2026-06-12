---
title: "can't browse the internet while downloading"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by didooofidooo on 2008-09-02
hi everybody
i have a problem with Ubuntu 8.04. when i start to download any file from the internet, it takes the whole bandwidth and i can't even browse a website. I'm using a 256 kbps ADSL line. 
this problem makes the internet useless while downloading!!
this problem doesn't happen in windows, so anybody can help?

---

### Post by jigsaws on 2008-09-02
Do you download it by ftp, http? Do you have DSL router with qos?

---

### Post by didooofidooo on 2008-09-02
it's not about http or ftp, because it happens in both even video streaming on youtube makes me not able to browse or download from the internet.
and about the router, I have a TP-Link TD-8840 ADSL2+ Router
but if the problem is in the router, so why it's not happening in windows running in VirtualBox on the same computer??

---

### Post by jigsaws on 2008-09-02
Your line is slow, and it is problem, but not as big as you described. Maybe you can tune it by queues length or kernel TCP parameters, but you can also try to use qos function of your router.

To be sure - you are not using any download accelerator?

You can test your problem by ping any internet host with and without downloading any file in the background. Check response times.

It can be problem with taking whole download or upload bandwidth.

You can also read more about QoS / Traffic Shaping. But the easiest way is using it at your router.

---

### Post by didooofidooo on 2008-09-02
thanks so so much jigsaws the problem is fixed just by enableing the QoS on the Router :D

---

