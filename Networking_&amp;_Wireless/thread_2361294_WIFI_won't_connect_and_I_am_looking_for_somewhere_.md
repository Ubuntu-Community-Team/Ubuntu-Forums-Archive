---
title: "WIFI won't connect and I am looking for somewhere to start as a new user!"
date: 2017-05-14
forum: Networking &amp; Wireless
---

### Post by gwilli10 on 2017-05-14
I connected to wifi originally and set my laptop up. I may have played with the wifi drivers by accident and now I am trying to connect to a different wifi and it won't connect. I am trying to figure out where to start looking into this as a new user. I posted some info below that may help.

Laptop is a Dell XPS (9360) that was bought with ubuntu already loaded. 

[TABLE="class: m_6534855722874181582MsoNormalTable, width: 418"]
[TR]
[TD][FONT=&amp][COLOR=#003366][FONT=Arial]Killer 1535 802.11ac 2x2 WiFi and Bluetooth 4.1 by Qualcomm

Side note: I am also getting an error on boot every once and awhile that says System program problem report that I haven't been able to explain either. 

If anyone can help that would be awesome.

[/FONT][/COLOR][/FONT][/TD]
[/TR]
[/TABLE]
 [TABLE="class: m_6534855722874181582MsoNormalTable, width: 418"]
[TR]
[TD][FONT=&amp][COLOR=#003366][FONT=Arial]Killer 1535 802.11ac 2x2 WiFi and Bluetooth 4.1[/FONT][/COLOR][/FONT][/TD]
[/TR]
[/TABLE]

---

### Post by Bucky Ball on 2017-05-15
Welcome. I'll reply to your older thread as the newer one will probably be closed soon as duplicate posting is not permitted here. ;)

Please give us the output of 

```
sudo lshw -C network
```

... for starters. Also, you say it worked to start but now won't work with another network. Does that mean it still works with the original network and you are having problems only with the new network???

A tip: One support issue a thread here. Remove the stuff about the system error and post a new thread about it UNLESS it started happening when you changed drivers. Avoids confusion. It appears to have nothing to do with this, though, and is probably related to another known issue that is easy to fix (or ignore). ;)

---

### Post by gwilli10 on 2017-05-15
Hi! Thanks for the tips. I ran the command requested and listed the output in the attached image. I am still able to automatically connect to the initial network but still have problems with the new network. It looks as if that command is recognising my wifi chip. Let me know if there are any other commands that can help be shared with you.

Cheers,

Greg

---

### Post by Bucky Ball on 2017-05-15
Okay, great. Well, as you connect to your home network automatically and everything works without issue, there is nothing wrong with your wireless and pointless looking there. There is a problem with connecting your working wireless with whatever access point (network) you are trying to connect to elsewhere.

Better tell us what network that is and what the exact problem is when you try to connect. What happens?

---

