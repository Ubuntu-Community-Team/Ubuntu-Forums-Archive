---
title: "Ndiswrapper works if boot with wifi switch on before boot"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by anthonws on 2007-11-24
Hello to all!

I'm running Gutsy 64Bit (ADM) with latest stable version of ndiswrapper (1.49).

My wifi card is a Broadcom 4312.

I can access my wlan0 interface (the alias that I created for ndiswrapper) only if I boot with the wifi switch on before starting Gutsy.

If I boot with it off and then switching it on, the interface wlan0 doesn't appear.

I've tried ndiswrapper -ma, modprobe ndiswrapper, I can see the module with lsmod and I get a error when trying to ifconfig wlan0 up (no such device)...

Could anyone give me a hand??

Is this normal or am I missing something?

Thanks.

Anthon.

---

