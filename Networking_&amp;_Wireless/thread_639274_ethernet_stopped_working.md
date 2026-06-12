---
title: "ethernet stopped working"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Ditto125 on 2007-12-13
Someone gave me a computer the other day and I decided to do a dual boot of Ubuntu Gutsy and XP Pro. I have another dual boot machine running the same two OSs, it's been running Ubuntu for a couple of years now, and 7.10 ever sicne a couple of days after it came out.I ended up getting some weird issue today when I booted into Ubuntu on this new machine.The ethernet just doesn't work, it works fine on XP (which is what I'm in now) but in Ubuntu the lights on the port don't even light up. The bizarre thing is that ethernet in Ubuntu works fine on the live disc and it worked fine for the past couple of days on my install. Anyone got any ideas as to how to fix it? I've searched here and on google and haven't found anything similar enough to try out a fix. A bit more information, XP reports the ethernet card as "Realtek RTL8139 Family PCI Fast Ethernet NIC".

---

### Post by hoppy on 2007-12-14
Hi,

Have you seen this thread:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

I had what seems to be the same problem and that just turning the machine of completely and then restarting worked wonders! Hope it helps.

Hoppy

---

### Post by GSF1200S on 2007-12-14
> **Ditto125 said:**
> Someone gave me a computer the other day and I decided to do a dual boot of Ubuntu Gutsy and XP Pro. I have another dual boot machine running the same two OSs, it's been running Ubuntu for a couple of years now, and 7.10 ever sicne a couple of days after it came out.I ended up getting some weird issue today when I booted into Ubuntu on this new machine.The ethernet just doesn't work, it works fine on XP (which is what I'm in now) but in Ubuntu the lights on the port don't even light up. The bizarre thing is that ethernet in Ubuntu works fine on the live disc and it worked fine for the past couple of days on my install. Anyone got any ideas as to how to fix it? I've searched here and on google and haven't found anything similar enough to try out a fix. A bit more information, XP reports the ethernet card as "Realtek RTL8139 Family PCI Fast Ethernet NIC".

Is this on a desktop? Do you use wireless at all? If not, we can just setup your computer to connect without network manager. I dont have a network manager on my lappie. If I connect an ethernet cable to it, it gets an IP almost instantly. 

Please post the contents/results of:

```
ifconfig
```

```
sudo gedit /etc/network/interfaces
```

```
lspci
```

and we'll go from there...

---

