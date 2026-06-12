---
title: "Realtek Ethernet connects and immediately drops on 16.04.01 LTS"
date: 2016-07-30
forum: Networking &amp; Wireless
---

### Post by sswarnkar13 on 2016-07-30
hello,
i am facing same problem please help me out
output of the commands are here.. [http://pastebin.com/irceqXvn](http://pastebin.com/irceqXvn)

---

### Post by jeremy31 on 2016-07-30
Moved to it's own thread from [https://ubuntuforums.org/showthread.php?t=2332210](https://ubuntuforums.org/showthread.php?t=2332210)

---

### Post by praseodym on 2016-07-31
Do you need the package filter (firewall)? If not, uninstall it:
```

sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

