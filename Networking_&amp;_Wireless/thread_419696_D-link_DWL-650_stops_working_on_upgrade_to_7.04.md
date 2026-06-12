---
title: "D-link DWL-650 stops working on upgrade to 7.04"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by x1101 on 2007-04-23
I had been running an install of Ubuntu 6.10 for a few months now, and since install my wireless card, a D-link DWL-650 was worked with no problems, but last night I upgraded to 7.04, and now the card is not even recognized (the card is usually found on wlan0)  anyone who has any ideas, help would be wonderful.


Thanks

---

### Post by thornomad on 2007-04-24
It seems to be broke in Feisty ... I am not sure if there is a fix yet ... haven't played with it yet (don't want to upgrade until I figure out how to make it work) ...

[http://ubuntuforums.org/showthread.php?p=2512758#poststop](http://ubuntuforums.org/showthread.php?p=2512758#poststop)

That links to the bug on launchpad.  Post your problem there.  Maybe someone can fix it.  I do not know how.

EDIT: Oh -- this is reference to the 650 ... the bug is for the 650+ ... I don't know if they use the same driver or not.  I suspect not.  Sorry.

---

### Post by emailgregn on 2007-04-24
I've had similar problems with this card. I found that by blacklisting the orinoco modules and using the hostap or prism2 drivers, things could be made to work. Start at /etc/modprobe.d/

Good luck

---

### Post by thornomad on 2007-04-25
> **emailgregn said:**
> I've had similar problems with this card. I found that by blacklisting the orinoco modules and using the hostap or prism2 drivers, things could be made to work. Start at /etc/modprobe.d/

Good luck

You referring to the 650 or the 650**+**?  Just curious because I haven't gotten the 650+ working either.

---

### Post by emailgregn on 2007-04-25
I was referring to the old DWL 650.

---

### Post by billycub on 2007-05-02
I have a DWL-650 (not the 650+) and the following got my card working. Open a terminal window, and enter the following:

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add the following line to the end of the file:

```
blacklist hostap_cs
```

This stops the hostap module from loading, and then the (working) orinoco driver gets used instead.  With this change, my DWL-650 works flawlessly.  Note that not all DWL-650's have the same chipset, so this may not work for everyone.

Good luck--

---

### Post by ouschmitz on 2007-05-10
I discovered that my D-Link DWL 650 was not working because the chipset it is based on is blacklisted by default in Feisty (it worked fine under Edgy).  I have Rev M (see the d-link support site to find your revision) and the Realtek 8180L chipset it uses is the problem. [ Here is a post that helped me]("http://ubuntuforums.org/showthread.php?t=422198") (actually I un-blacklisted the realtek driver - which it claims causes a kernel bug - so I should probably use the ndiswrapper instead)

---

