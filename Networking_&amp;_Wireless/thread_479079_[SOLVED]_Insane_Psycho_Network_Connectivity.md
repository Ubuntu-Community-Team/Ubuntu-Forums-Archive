---
title: "[SOLVED] Insane Psycho Network Connectivity"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by brion@cbkidder.com on 2007-06-19
[B]WTF Ubuntu?

Every time I boot up my laptop I spend AT LEAST a half an hour to 45 minutes trying to persuade you to connect to the network! Tonight I booted up at 8pm hoping to do some work but OH NO neither the wired nor the wireless would deign to recognize the connection. Windows can see the router no problem and even ask politely for a DHCP address; surely you're better than Windows, aren't you?

WTF? After three reboots, four or five togglings of the router power, and countless futile attempts to configure the connection properties, there was STILL no connection until all of a sudden your psychotic borderline personality led you to grant me connectivity without any rhyme or reason whatsoever. 

WTF Ubuntu? At least you're better than Mandriva but is that really saying much?

I want to be able to boot up my laptop, have both the wired and wireless connections that were working JUST FINE when I shut down to resume operation without all this hassle. Is that unreasonable? WTF? Thanks for yet another wasted evening.

Brion Kidder
Orange, California
Dell Inspiron 1100 running Edgy again because Feisty didn't work
Linksys WPC54G v3 wireless card[/B]

---

### Post by marc321 on 2007-06-20
This might help you: [http://antonym.org/node/89]("http://antonym.org/node/89")

I was about to type a lot of that info in when I found that page.  It sounds like you are using the default bcm43xx module, which is very, very buggy, especially for newer wireless cards.  With my Linksys WMP54G, the bcm43xx gave me a connection, but it was very unstable.

Basically, you'll have to install ndiswrapper, download the appropriate Windows drivers for your card (dreadful, I know), and set up ndiswrapper.  This page describes the process fairly well, although one little important bit was left out.  At any point in the process, open up /etc/modprobe.d/blacklist and add bcm43xx to the end.

```
echo "bcm43xx" >> /etc/modprobe.d/blacklist
```

You don't want ndiswrapper and bcm43xx fighting to use the same card. ;)

Good luck!

---

### Post by marc321 on 2007-06-20
> I want to be able to boot up my laptop, have both the wired and wireless connections that were working JUST FINE

Sadly, many hardware manufacturers don't release the full specs for their hardware, so people can't make high quality open source drivers without a lot of reverse engineering.  Hopefully Dell/Ubuntu and Shuttleworth will help with that.

---

