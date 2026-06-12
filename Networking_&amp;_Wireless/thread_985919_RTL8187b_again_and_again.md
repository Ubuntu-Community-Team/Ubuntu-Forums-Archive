---
title: "RTL8187b again and again"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Brown_ on 2008-11-18
Hi y'all,
There ara a lot of users using the RTL8187b wifi card, by now, the only way to have it working is using ndiswrapper(it aint a good solution for me) and the cuervo modified driver, if I aint wrong, both solutions only connect on WEP connections; the question is, why doesnt the ubuntu team take a better look for that issue?
The only reason i gave up on ubuntu was due to wireless troubles... :mad:

---

### Post by renzokuken on 2008-11-18
I've always had trouble with this chipset on my laptop, to the point where i use windows if i need wireless now.

The only time i ever had it working was using the Win98 driver under Ndiswrapper.

Never tried the Cuervo driver but you need to make sure you have correct patched version for your kernel.

However, as of kernel 2.6.27, the native built in driver is supposed to work but i never had it working. Would cut out after 5 or 10 minutes, sooner if downloading heavily.

Hopefully it will get sorted soon because its a real crippler for my laptop and linux.

EDIT: and you are right, when i did have it working, WPA never worked (not even an option) but WEP did. I think i used WICD instead of Network Manager too.

There are plenty of bugs filed against this problem but no real solution yet.

---

