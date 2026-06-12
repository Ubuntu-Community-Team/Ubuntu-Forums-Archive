---
title: "Belkin F5D8055 V2 Wirless USB Adapter"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by drumstik102 on 2009-09-29
i had given up trying to get my wireless adapter (Belkin F5D8055 V2) to work but i really need it.  has anyone successfully gotten this model to connect to a network?

so far Ive installed the rt2870 driver and my system recognizes the hardware (ra0) and the blue LED on the stick lights up and flickers, but i cant get it to find my wireless network.

---

### Post by mikeyphi on 2009-09-29
This might provide the answer: 
[http://ubuntuforums.org/showthread.php?p=7510417#post7510417](http://ubuntuforums.org/showthread.php?p=7510417#post7510417)

---

### Post by drumstik102 on 2009-09-29
yeah i have tried all that but it seems like V2 needs additional steps. someone in that thread wasnt able to connect with their V2 either.

---

### Post by drumstik102 on 2009-10-02
Bump

---

### Post by jcurtis71 on 2009-11-15
Has anyone progressed further with this? I've got a F5D8055 v2 and can't get it going on 64bit Ubuntu 9.10.  either ...

---

### Post by gannggstaz on 2010-01-21
I've finally done it after about 2 weeks of near random experimentation:
[http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426](http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426)
It works perfectly, though I haven't checked if there's any problems with connection speed.

---

### Post by tvrtuscan on 2010-02-21
Great to hear you did get it to work.  What Network Manager are you using?  Does it scan ok?

If I run iwlist ra0 scan it just displays 'No scan results'.  Did you have to set anything else up?

I'm using the ralink 2.3 driver.

---

### Post by perrya on 2012-04-13
[Solution found !!!]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html#comment-179810")

---

### Post by oldos2er on 2012-04-14
Closed, necromancy.

---

