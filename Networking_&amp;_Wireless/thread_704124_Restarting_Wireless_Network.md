---
title: "Restarting Wireless Network"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by MDKSIGN on 2008-02-22
Hi! My first post and problem with Ubuntu so far. My problem is when I boot up into Ubuntu 7.10 I connect instantly to my wireless router, no problems, but after a couple of hours or so I get disconnected (the router is still connected to the internet) and I can't connect back to the router, I have to reboot the whole computer, which it then works fine again.

If you know why please help! Also would restarting the network manager help (I don't know how to do this)?

- MDK.

---

### Post by jan quark on 2008-02-22
you can try to restart the network with this terminal commmand

```
sudo /etc/init.d/networking restart
```

---

### Post by gvrijswijk on 2008-02-22
Exactly the same problem here. It seems to be worse when the connection is highly active (downloading, etc). Gutsy is the only distro I seem to be having the problem with (tested Fedora, Gentoo and Hardy).

Unfortunately
```
/etc/init.d/networking restart
```
doesn't help either.

---

### Post by WakkiTabakki on 2008-02-22
Having the same problem aswell... 
Restarting /etc/init.d/Networking does not help unfortunately...


/N

---

### Post by gvrijswijk on 2008-02-22
If you use a card with a RT61from RaLink, find the guide for installing ndiswrapper on this forum. I did and my wireless now works flawlessly.

---

