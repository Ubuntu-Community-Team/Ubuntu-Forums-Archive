---
title: "Palm - Bluetooth"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by esquilo on 2006-10-12
Hi Guys, I need your help.

I use this commands everytime when i want connect my palm in internet at PPP conection with bluetooth:

dund --listen --persist --msdun call dun
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i ppp0 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT


How can I make this things automatic?

---

### Post by devnulljp on 2006-10-12
Good article in LJ about syncing a treo via BT: [http://www.linuxjournal.com/node/8185/print](http://www.linuxjournal.com/node/8185/print)

Worked for me.

---

