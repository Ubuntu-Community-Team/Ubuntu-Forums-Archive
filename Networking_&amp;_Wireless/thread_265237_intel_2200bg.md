---
title: "intel 2200bg"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by foureight84 on 2006-09-25
back when dapper drake was in beta, i remember that there was a thread with download to a script that installs the 2200bg drivers automatically. does anyone remember what i am talking about? i can't seem, i'm hoping you could help.

---

### Post by reacocard on 2006-09-25
the 2200 is supported out of the box on dapper (and edgy). no need to separately download and install drivers.

---

### Post by civetta on 2006-10-01
> **reacocard said:**
> the 2200 is supported out of the box on dapper (and edgy). no need to separately download and install drivers.

I just switched to edgy from dapper. My wireless card used to be listed as 2200bg and now is listed correctly as 2915abg. But now I no longer get wireless signals. I want the 2200 drivers back!

---

### Post by civetta on 2006-10-01
Wait,

excuse me, I'm new to this. My lsmod shows me using ipw2200 but I'm not sure why it's stopped working with edgy.

---

### Post by danielinthelionsden on 2006-10-02
Hi, I was experiencing the same problem with the same hardware.  I don't know if it's related to your issue but I discovered that on my laptop the "fn" + "wifi" button combination had turned off the wifi card.

My "/var/log/messages" log reflected this message:

Oct  2 08:37:22 dvlatlinux kernel: [17179588.768000] Kill switch must be turned off for wireless networking to work.

Pressing the "fn" + "wifi" combination fixed everything.

---

### Post by civetta on 2006-10-09
All I needed to do in the end was install network manager and comment out all the interfaces except for lo in /etc/network/interfaces.

Now I'm cruisin'. For some reason, I never was able to activate my wireless connection using the gui tool in System -> Administration -> Networking though... wierd, but network manager was the answer to my gui troubles.

---

### Post by Linuturk on 2006-11-07
I have problems with the same hardware using the gnome Networking GUI. It doesn't display a list of networks that are available. Any help?

---

### Post by m47h3us on 2006-11-07
yeah i have same probblem its working just not lol so annoying :(

---

