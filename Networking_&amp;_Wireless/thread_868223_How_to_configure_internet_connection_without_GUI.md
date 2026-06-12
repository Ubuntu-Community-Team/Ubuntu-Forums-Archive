---
title: "How to configure internet connection without GUI?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by orphefs on 2008-07-23
Hi, 

just installed my Ubuntu distro (yes, another newbie, heh) and I am having trouble connecting to the internet...specifically:

I have a Speedstream router which is connected via USB to my laptop runnning Windows XP. It uses a PPPoE connection. I have tried to connect the Ethernet port of the router to my Ubuntu desktop PC, and I run pppoeconf, and it finds eth0, but then it cant configure anything, because the "Access Concentrator of provider did not respond" and that there might be another running pppoe process which controls the modem. Then I tried disconnecting the USB plug from my Windows laptop and restarted the modem, still didn't work!!!

If it helps at all, here is my MSDOS ipconfig output:

[[IMG]http://img381.imageshack.us/img381/3924/ipconfignk9.th.png[/IMG]](http://img381.imageshack.us/my.php?image=ipconfignk9.png)

What to do next? I've looked online but couldn't find anything that helped!

Thanks in advance for your help!:)

---

### Post by PinkFloyd102489 on 2008-07-23
Network Manager is just a frontend editor to /etc/network/interfaces. Check there.

---

### Post by orphefs on 2008-07-24
hey, how do I open that? (don't forget I am fresh into Linux)

---

### Post by tinny on 2008-07-24
> **orphefs said:**
> hey, how do I open that? (don't forget I am fresh into Linux)

Read only
```

vim /etc/network/interfaces

```


Read write
```

sudo vim /etc/network/interfaces

```

I wish I could help more, what is the full model name of the modem?

---

### Post by orphefs on 2008-07-24
Hey, I originally changed my /etc/network/interfaces file, but then I noticed after running pppoeconf that it chenged to this:

--------------------------------------------------------
iface eth0 inet dhcp



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig help up | line maintained by pppoeconf
provider dsl-provider

auto help 
iface help inet manual

--------------------------------------------------------

Model specs are:


What to do next??:confused:

thanks:)

Siemens SpeedStream 4200
Ethernet/USB ADSL Modem

---

### Post by orphefs on 2008-07-24
then should I rather use Windows to get on the internet?? :)

---

### Post by JediKnight on 2008-07-26
When you don't get satisfactory answers, yes, I am afraid so :)

I can't connect from my Linux either and fell into oblivion.

---

