---
title: "Tl-wn851nd issues"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by adrisilversun on 2014-02-28
Hello friends, today I installed ubuntu 13.1 and everything worked perfectly, but it seems that i'm finding some compatibility problems with my Wireless PCI Adapter TP-LINK TL-WN851ND.

Ubuntu connects to my router and works perfectly fine, but after about 10 minutes, i don't recieve any data (although Ubuntu is still connected). If I manually disconnect,  i can't connect to my router again (ubuntu asks for the password again and again).

Can anybody help me? I'm not an advanced Ubuntu user and I couldn't find any help in Google (i'm not a native speaker).

Thank you in advance.

---

### Post by praseodym on 2014-03-01
Hi,

there are still a lot of problems with this card. Lets check
```

lspci -nnk | grep -iA2 net
iwconfig
lsmod
cat /etc/resolv.conf
ifconfig -a
iwlist chan
sudo iwlist scan
```

You may want to check:```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo /etc/init.d/networking restart
sudo service network-manager restart

```

---

