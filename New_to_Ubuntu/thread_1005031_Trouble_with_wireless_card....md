---
title: "Trouble with wireless card..."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by c.e.mcbride.iv on 2008-12-07
:mad:

using ubuntu on a dell latitude 610 and attempting to get access to my wireless network.  my wireless router is a linksys wrt54g, i believe.  its the black and blue one with the little stubby legs where you can stack them up easily.  using no security on router except mac filtering.  my wireless card:  belkin wireless g card.  it sees the network.  but no communication whatsoever.  anyone got any answers?

---

### Post by nhasian on 2008-12-07
in a terminal type

```
iwconfig
```

does it show that your connected to your linksys router?  (the same one that was on south park hehe)

[IMG]http://www.blogcdn.com/www.engadget.com/media/2008/04/screen-grabs-linksys-internet.jpg[/IMG]

also enter in a terminal:

```
ifconfig
```

for your wlan0 what ip address do you have?  something like 192.168.x.x

can you ping the router?

---

### Post by newbee70 on 2008-12-07
> **c.e.mcbride.iv said:**
> :mad:

using ubuntu on a dell latitude 610 and attempting to get access to my wireless network.  my wireless router is a linksys wrt54g, i believe.  its the black and blue one with the little stubby legs where you can stack them up easily.  using no security on router except mac filtering.  my wireless card:  belkin wireless g card.  it sees the network.  but no communication whatsoever.  anyone got any answers?

you have been into ** Administration / Hardware drivers and activated it. **

have you left clicked on your network connection Icon

it should show there click on wireless and tell it to connect.

if you have wep or wpa set it will ask for your phase phrase.

and it will ask something like 40/128 wep ** however you have set the router**

hope this helps.

---

### Post by JAYCEE1 on 2008-12-07
You can also post on this thread the output of 

```

sudo lshw -C network

```

---

