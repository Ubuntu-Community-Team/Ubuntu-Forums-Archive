---
title: "Help Using Aircrack-ng on Ubuntu"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Nosss on 2008-12-07
Hi,
I am new to Ubuntu and all its code. so forgive me in advance. I am testing the strength of my Wireless home network. Now I can do everything up till the point of "sudo airodump wifi0" it comes up with a list of wireless networks, obviously mine is on there. however the problem is that the PWR of all the networks are -1...now i have seen other examples online and none imply it should show -1 so I was wondering do i have to enable the power somehow or is there an actual fault with the software? I am running on dual boot with vista. Using Ubuntu 8.10. I patched a driver onto my intel pro wireless 3945abg, Ipwraw which supports packet injection. I did test packet injection and it said successful. Thanks In advance.

Nos

---

### Post by taseedorf on 2008-12-10
testing the strength of your wireless? Quit lying.
haha
Anyways, you must turn on scan mode i believe....don't know command off hand, but you can google it.

iwconfig wlan0 mode scan

?

something similar

---

### Post by Nosss on 2008-12-12
hahaha, Thanks :D

---

### Post by taseedorf on 2009-01-12
should be mode monitor 

sorry

---

### Post by binbash on 2009-01-12
Did you enable monitoring?Which steps did you follow?

---

### Post by HunterThomson on 2009-01-12
I cracked my wep 128 with no clients. Boy is WEP weak.... Then cracked the AP's username/password with medusa.

---

### Post by binbash on 2009-01-12
> **HunterThomson said:**
> I cracked my wep 128 with no clients. Boy is WEP weak.... Then cracked the AP's username/password with medusa.

Wep does not need a client to be cracked

---

### Post by HunterThomson on 2009-01-12
> **binbash said:**
> Wep does not need a client to be cracked

I know that is how I did it....

---

### Post by akimatsu123 on 2009-01-12
We seem to have deviated from the original topic, but you can enable monitor mode with:

sudo airmon-ng start wlan0

that will create a new "mon0" connection that you can then use:

sudo airodump-ng mon0

---

### Post by hyper_ch on 2009-01-12
there's a good howto on this in the Tutorials section provided by Wieman01

---

