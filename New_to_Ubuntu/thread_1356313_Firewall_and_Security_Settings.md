---
title: "Firewall and Security Settings"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-15
Where are these located in the GUI? Where would I go if I wanted to block specific ports or services? Thanks

---

### Post by bodhi.zazen on 2009-12-15
The default application to configure your firewall is ufw. If you want a graphical application use gufw :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by Diametric on 2009-12-16
So there is no native firewall/port management tool in Ubuntu?  I'm surprised.  I don't follow how that decision was made.  Thanks anyway for the reply...much appreciated.  I'll look into the GUI you link to.

---

### Post by bodhi.zazen on 2009-12-16
Than "native" application is netfilter which is configured with iptables.

Most users find iptables to have a steep learning curve, but if you prefer :

[http://bodhizazen.net/Tutorials/iptables/index.html](http://bodhizazen.net/Tutorials/iptables/index.html)

---

