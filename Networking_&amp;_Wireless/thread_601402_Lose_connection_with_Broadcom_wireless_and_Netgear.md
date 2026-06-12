---
title: "Lose connection with Broadcom wireless and Netgear DG834GT router"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by DrewB on 2007-11-03
Hello, I'm using verison 7.10 of Ubuntu with a Gateway MX6440 AMD64 laptop.
The wireless network card is Broadcom BCM4318.
I am using Network Manager to connect to a Netgear DG834GT router provided by Sky (not my choice I hasten to add!)

If I'm close to the router in the office, within 1 or 2 meters, I can connect fine and it stays connected.

However if I'm further away, say in my bedroom or in the front room it takes several attempts to connect and then when it does finally connect the connection is *really* slow and usually drops after a few minutes and then I have to reboot in order to connect again. Not really ideal.

In the Device Manager it tells me that info.liux.driver is "bcm43xx"

Should I be using ndiswrapper?

It seems a shame when everything seems to work fine when I'm close to the router.
I don't get this problem with Windows by the way. And I also haven't had this problem in Ubuntu with other routers.

Any help would be greatly appreciated.
Thanks
Andy

---

### Post by kevdog on 2007-11-03
I would definitely recommend ndiswrapper/winxp driver for your situation.  Ive seen now in numerous posts about people complaining with range with their broadcom bcm43xx driver -- most were resolved with ndiswrapper.

---

### Post by DrewB on 2007-11-03
Ok thanks kevdog, I'll give it a go, much obliged.

---

