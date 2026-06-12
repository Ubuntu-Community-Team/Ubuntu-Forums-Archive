---
title: "First install - wifi not working"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by mark249 on 2015-09-25
Hello, I have installed Ubuntu on my laptop. It has win 7 already installed on win wifi works well. Sadly on ubuntu wifi doesnt work. I can connect.but.no internet. Even ping doesnt work. Please can someone help? Iam beginner

---

### Post by Frogs Hair on 2015-09-25
Hello and Welcome Mark:

I'm moving to networking & wireless

---

### Post by praseodym on 2015-09-26
Hi,

please run the wireless-script from the sticky-thread and show the output here.

---

### Post by mark249 on 2015-09-26
Hello, here are results: [http://pastebin.com/K5xjNaiH](http://pastebin.com/K5xjNaiH)

---

### Post by praseodym on 2015-09-27
Please run:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
and reboot.

---

### Post by mark249 on 2015-09-27
> **praseodym said:**
> Please run:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
and reboot.
Hi, thanks for reply. Sadly, it just asked for password and then echoed that options rtl... after reboot still no internet access.

---

### Post by praseodym on 2015-09-27
Try deactivating IPv6 in the network manager settings, change to a fixed channel in your router

---

### Post by mark249 on 2015-09-27
? Its not my router, I just need to connect to wifi, in windows it works, in ubuntu it doesnt -its connected but no internet. Its ubuntu fault, because in edora it works - I need ubuntu though

---

### Post by praseodym on 2015-09-27
Please ask the owner if a MAC-address filter is activated. Also try
```

echo -e "nameserver 8.8.8.8\nameserver 8.8.4.4\nnameserver 192.168.0.1" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by mark249 on 2015-09-27
Ca you tell me why I did that.echo? It just wrote what I wrote... and wifi still not working... network restart doesnt helped

---

