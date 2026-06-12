---
title: "Best firewall GUI for desktop?"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by superarthur on 2010-03-22
I want to set up a firewall. I looked into the software centre and there are quite a few choices. I just want one that is easy to set up and relatively secure (to me, simplicity is the main factor). Which one is the best?

---

### Post by linuxman94 on 2010-03-22
gufw is a GUI interface for the default ubuntu firewall.  Install it by opening synaptic (System -> Administration -> Synaptic Package installer) and searching for gufw.  Mark it for install and click apply. After it is done, it will be in System -> Administration.

---

### Post by spartan_87 on 2010-03-22
Iv used Firestarter for awhile now. It has a really easy gui and seems to be pretty secure. You can find it in synaptic.

---

### Post by bodhi.zazen on 2010-03-22
Are you sure you even need a GUI ?

Open a terminal and enter:


```
sudo ufw enable
```

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Firestarter is popular, but unmaintained and bugs go un addressed, so if you have problems with firestarter you may be out of luck.

Last, firestarter conflicts with ufw, lol

---

