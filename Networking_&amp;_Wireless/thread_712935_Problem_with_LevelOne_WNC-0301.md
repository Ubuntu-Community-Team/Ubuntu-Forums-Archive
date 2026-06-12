---
title: "Problem with LevelOne WNC-0301"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by kamiar on 2008-03-02
Hi
My wireless card is LevelOne WNC-0301. When I switch to Ubuntu from MS Win can't connect to internet, ubuntu recognition networks around me with signal quality but can't connect to them.
In win I can connect with this settings: IP & Gateway & Subnet Mask in IPv4 section, the network is open and not encrypted with WEP and other.
When I ping Gateway IP ubuntu say "Network is unreachable"
Also I run Ubuntu in live mode.

Can you help me?
Sorry, my English is too poor :(

---

### Post by Brain-free on 2008-03-14
Hey Kamiar, I have the same card as you and experienced roughly the same problems. So, I can probably help you... :-)

First things first, what version is the Ubuntu you're running? (I managed to make mine work under Ubuntu 7.04 and & 7.10)

EDIT: (screw that, now I saw what's your version.)

So what worked for me is :1) getting the [latest drivers]("http:/http://global.level1.com/technical.php?Id=16&Type=All&SearchName=WNC-0301"), 2) installing them through ndiswrapper (I believe you have done those steps already) and finally typing in the terminal:

```

sudo gedit /etc/modprobe.d/blacklist

```

and once inside the blacklist file add in the last line:
```

blacklist r8180

```
and then save. It's a simple command, totally reversible. 

After completing this, In my PC, the wireless network jumped into my screen. I guess r8180 is a faulty driver and by blacklisting it, this bug is fixed. Hope this is the same case with you!

---

### Post by demkpap on 2008-03-16
Thank you Brain-free. Your suggestion has solved my problem with  WNC-301. I had spent a couple of days on it.

---

### Post by kamiar on 2008-03-27
Thank you Brain Free, I will test this way tonight :)
1 question! This way work in live mode?

---

### Post by Brain-free on 2008-03-27
OK, that's a tough one. Well, I haven't tested it in live mode so I can't really tell you. However, since it's just a blacklisting, I believe it will. I'd suggest you try it anyway since it is reversible. 

Tell me if it worked!

---

