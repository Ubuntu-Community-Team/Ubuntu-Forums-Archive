---
title: "Permissions to change bluetooth settings"
date: 2019-10-05
forum: Networking &amp; Wireless
---

### Post by seriouslysupersonic on 2019-10-05
I have a Logitech MX Anywhere 2S wireless mouse that suddenly became very laggy on ubuntu (works fine on Windows).

I read about this issue here [https://forum.manjaro.org/t/bluetooth-mouse-lag/99386](https://forum.manjaro.org/t/bluetooth-mouse-lag/99386) and it was suggested to change some bluetooth settings using:

```

[COLOR=#121112][FONT=&amp]$ su 
$ echo 0 > /sys/kernel/debug/bluetooth/hci0/conn_latency 
$ echo 6 > /sys/kernel/debug/bluetooth/hci0/conn_min_interval 
$ echo 7 > /sys/kernel/debug/bluetooth/hci0/conn_max_interval[/FONT][/COLOR]

```

When I tried these commands I realized I cound't use su on ubuntu and used

```

$ sudo -s

```

However, I still get
 
```

zsh: operation not permitted: /sys/kernel/debug/bluetooth/hci0/conn_latency

```

How can I change these settings? The laggy mouse is really bothering me...

Thanks in advance!

---

### Post by Xian on 2019-10-05
If sudo does not cover the entire redirection it cannot be fully executed as root. 

For example try this command format instead:

```
sudo sh -c "/bin/echo 0 > /sys/kernel/debug/bluetooth/hci0/conn_latency"
```

---

### Post by seriouslysupersonic on 2019-10-16
> **Xian said:**
> If sudo does not cover the entire redirection it cannot be fully executed as root. 

For example try this command format instead:

```
sudo sh -c "/bin/echo 0 > /sys/kernel/debug/bluetooth/hci0/conn_latency"
```


Thank you for the suggestion, but I still get 

```
sh: 1: cannot create /sys/kernel/debug/bluetooth/hci0/conn_latency: Operation not permitted
```

Any ideas how to circumvent this?

Ragerds

---

### Post by slickymaster on 2019-10-16
*Thread moved to **Networking & Wireless**.*

---

