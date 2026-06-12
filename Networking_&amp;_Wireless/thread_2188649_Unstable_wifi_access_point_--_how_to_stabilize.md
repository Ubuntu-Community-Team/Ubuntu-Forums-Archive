---
title: "Unstable wifi access point -- how to stabilize?"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2013-11-18
I'm having quite remarkable problems establishing a connection between my tablet and my computer.

Tablet: Asus transformer pad TF300T, Android 4.2.1
Computer: Ubuntu 12.04

Linux dlm-A6200 3.2.0-56-lowlatency #58-Ubuntu SMP PREEMPT Tue Oct 29 16:14:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Wifi card: Qualcomm Atheros AR9285

I've tried doing it through my home wifi router. Unfortunately, while this worked once upon a time, now it isn't working (or it works only sporadically... *very* sporadically). In another thread on these forums, I was told to disable AP isolation... which I just tried to do, but 192.168.1.1 is not responding. I can't get to the admin page.

I had also found a script [1] which purports to set up an access-point hotspot Linux, to which Android can connect. This works exactly once per boot. (Since it works at all, I'm certain the AR9285 supports this use.)

```
sudo service wifi_access_point start
```

^^ may or may not actually start the access point. If not, running it a second time will do it.

```
sudo service wifi_access_point stop
```

^^ The access point disappears, and the computer reconnects to the home router. So far so good.

```
sudo service wifi_access_point start
```

^^ The access point reappears and Android tries to connect to it. But it never gets an IP address.

So I suppose the service installed by the script is not handling isc-dhcp-server properly. But I'm way out of my depth and I have no idea how to troubleshoot this.

I need to get this working very quickly, or I'll have to change some plans for a performance on Friday. Or buy another wifi router (which might then magically enable AP isolation, without any action from me, and then not let me into the admin page).

Thanks in advance,
hjh

[1] [https://gist.github.com/dashohoxha/5767262](https://gist.github.com/dashohoxha/5767262)

---

### Post by dewdrop_world on 2013-11-18
Well, we can downgrade this question away from "emergency." It turns out that setting up a tethering hotspot on my tablet Just Works (TM) and seems reliable. That will suit my purpose -- I don't need Internet access, only device-to-device communication.

I'm still curious why the earlier-referenced script, which seems to be doing the right things, doesn't actually work a second time without rebooting Linux. Any ideas?

(One reason why that would still be useful for me is that many Chinese hotels offer an ethernet connection, but very poor -- or no -- wifi. It would be great to be able to run my phone and tablet through my computer if I'm forced into that situation.)

hjh

---

