---
title: "dialup disconnection problem"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by pr_009 on 2006-10-26
I have ubuntu dapper installed on my system and since i have a lucent modem so i have also installed ltmodem drivers on my system and everything went well.
I use wvdial to connect to the internet but the problem is that my connection hardly remains established for 15 to 20 minutes and then it disconnects automatically.
I was reading some threads in linux networking section of linuxquestions.org and there a person having the same problem with his ethernet connection fixed his problem by tweaking the iptables and probably doing something with the 'timeout' variables.
Plz help me fix this problem somehow. If the problem lies in iptables, do guide me how to correct it cuz i'm not an expert..........thanx in advance

---

### Post by towsonu2003 on 2006-10-26
unless you installed a firewall package yourself (firestarter, guarddog etc), your iptables is empty (you don't have a firewall) => I doubt it about your firewall.

check out this link, especially the options it suggest to be put into the wvdial.conf: [https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb)

---

