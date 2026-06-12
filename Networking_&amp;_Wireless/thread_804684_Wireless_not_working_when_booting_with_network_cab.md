---
title: "Wireless not working when booting with network cable plugged in"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by mcapurro on 2008-05-23
Hi!

I have an Acer Aspire 5520 with Ubuntu 8.04 (Hardy) 64bits. I managed to have wireless working with ndiswrapper. I also installed the wpa_supplicant, though I did not configure it. The problem I'm facing is that when the machine boots and I have the network cable plugged in, if I want to connect to a wireless network, I can browse the available wireless networks but I'm not able to connect to any of them (WPA, WPA2). With dmesg i got the following error:

ADDRCONF(NETDEV_UP): wlan0: link is not ready

What's interesting is that if I boot the machine with the network cable unplugged, I'm able to connect to the wireless network (and have full access to the intranet and internet). I assume the problem has to do with something that is loaded when the Wired Network is first detected and configured.

Thanks!

Bye

---

### Post by mapes12 on 2008-05-23
A hard wired device takes priority over wireless. You need to take the cable out to avoid IP address conflicts etc. with your router. There may be  way / script to take down the ethernet adaptor but I haven't seen one.

---

### Post by mcapurro on 2008-05-23
> **mapes12 said:**
> A hard wired device takes priority over wireless. You need to take the cable out to avoid IP address conflicts etc. with your router. There may be  way / script to take down the ethernet adaptor but I haven't seen one.
Thanks for the reply. The problem is not that I want to be connected first to the wireless network. The problem is that when connected to the Wired Network first, then I cannot connect to the wireless, even if I disconnect the cable. I believe a service or module is loading when the Wired Network starts up that is preventing the wireless network from connecting after that.

---

### Post by mapes12 on 2008-05-23
> managed to have wireless working with ndiswrapper

ndiswrapper can be very unreliable. What wireless adapter do you have?

```
sudo lshw -C network
```

Also, try disabling your ethernet interface:

```
ifdown eth0
```

where eth0 is your ethernet adapter from the output of sudo lshw -C network

then restart network services:

```
sudo /etc/init.d/networking restart
```

---

### Post by Steve413z on 2008-05-23
the package "laptop-net" might help you
I know my laptop has a weird problem, where if you don't have the wired network plugged in when you boot, and you plug in later, it won't work. So you MUST boot with it plugged in to work.  But "laptop-net" fixed that, so maybe "laptop-net" might help you.

---

