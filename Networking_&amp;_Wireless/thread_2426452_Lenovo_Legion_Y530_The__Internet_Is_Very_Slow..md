---
title: "Lenovo Legion Y530 The  Internet Is Very Slow."
date: 2019-09-09
forum: Networking &amp; Wireless
---

### Post by phanthaiduong22 on 2019-09-09
I have just installed ubuntu dual boot with windows 2 days ago.
But the same wifi. But speed in windows better than ubuntu.
Here is my wireless script:
[https://pastebin.com/2CtvRyuQ](https://pastebin.com/2CtvRyuQ)

---

### Post by praseodym on 2019-09-09
Do you need the firewall?

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```Reboot

---

### Post by phanthaiduong22 on 2019-09-09
i feel that the internet is better a little. But it is still slow.
Some times, i get :
[h=1]"This site can&#8217;t be reached"
Here is my new script:[https://pastebin.com/bm28HEpG](https://pastebin.com/bm28HEpG)
Thanks[/h]

---

