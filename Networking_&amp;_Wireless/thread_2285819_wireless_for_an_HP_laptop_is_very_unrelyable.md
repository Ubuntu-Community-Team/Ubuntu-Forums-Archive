---
title: "wireless for an HP laptop is very unrelyable"
date: 2015-07-08
forum: Networking &amp; Wireless
---

### Post by SandroBoehme on 2015-07-08
Hello,

we have an HP laptop with Ubuntu 14.04 installed but the wifi usually does not fully work. After a reboot it works sometimes. Sometimes (rarely) the wifi connection is there but there is no internet connection. 
Please see here for the result of the wireless script:
[http://pastebin.ubuntu.com/11841604/](http://pastebin.ubuntu.com/11841604/)

Any help is much appreciated!

Best,

Sandro

---

### Post by praseodym on 2015-07-08
Try these module parameters

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot.

---

### Post by SandroBoehme on 2015-07-09
Thanks for looking into our issue and for your script Praseodym! Sadly  the wifi still does not connect after executing and rebooting.

---

### Post by praseodym on 2015-07-09
You need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by SandroBoehme on 2015-07-14
Thanks for your time Praseodym! In the mean time the wifi connection seems to work but sadly the internet connection is still very unrelyable. At one time the ping loses all packages and at the next ping command (with no change or command in between) it transmits data. The ping time is then either around 25ms or around 1050ms but nothing in between. This is the same with the resolv.conf change you sent us and without the change.
Any other ideas are highly welcome!

Thanks again,

Sandro

---

### Post by praseodym on 2015-07-14
Deactivate IPv6 in the network-manager profile and show
```

sudo iwlist scan
dmesg | grep country
```

---

