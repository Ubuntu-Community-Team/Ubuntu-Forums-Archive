---
title: "IBM T30 Wireless not working under linux"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by azzo2 on 2014-03-29
Hi, im using xubuntu 13.10. I tried several other distros but wireless is not working with my old ibm t30. Xubuntu finds the wifi spot, but can't connect to it; it is greyed out. I know that it is not hardware related because wireless works with Windows Xp out of the box.

 [ATTACH=CONFIG]251573[/ATTACH]

---

### Post by tgalati4 on 2014-03-30
Open a terminal and post the output of:

```
grep wireless /var/log/syslog
grep wireless /var/log/syslog.1
```

You will have to do some research to determine exactly which wireless card came with your computer.  IBM supplied at least 2 different cards for that machine.  Because of age, many have been replaced with faster cards.

[http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)

---

### Post by chili555 on 2014-03-30
> **tgalati4 said:**
> Open a terminal and post the output of:

```
grep wireless /var/log/syslog
grep wireless /var/log/syslog.1
```

You will have to do some research to determine exactly which wireless card came with your computer.  IBM supplied at least 2 different cards for that machine.  Because of age, many have been replaced with faster cards.

[http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)As well, and I suspect this is the real issue, many older cards are not capable of WPA. If the access point is set to WPA2, and it ought to be, the card will not connect. Check:```
iwconfig
```Is your wireless interface named eth1?```
sudo iwlist eth1 auth
```Do you see something like this?```
Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
```By the way, Thinkpads are whitelisted, meaning only authorized cards will work: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

---

