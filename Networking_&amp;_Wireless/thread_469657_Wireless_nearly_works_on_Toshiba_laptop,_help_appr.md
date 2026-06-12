---
title: "Wireless nearly works on Toshiba laptop, help appreciated."
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Jason Pettitt on 2007-06-10
Hi.
I've got a Toshiba Satellite laptop which I dual boot Windows (Vista, it really is ghastly) and Ubuntu (feisty). Ubuntu worked really well straight out the box but does have an irritating hiccup with wireless.

Basically internet works nearly all the time, and I can send email, but some websites fail to materialise (I can't search ebay for example) and I can't send email wirelessly. With a standard wired connection there's no problem, everything works; and the wireless works with windows just fine too.

Ubuntu auto-detected an Intel Pro 3945 wireless network connection and installed the restricted drivers. I've tried switching off ipv6 in /etc/modprobe.d/aliases but to no avail.

---

### Post by cptcrunch on 2007-06-10
what kernel are you using? If you updated to the latest kernel 2.6.20-16 then yes this kernel update will break your wireless connectivity. I recommend 7.04 feisty with the 2.6.20-15 kernel and you wireless should work. There was a bug report filed, but I can't get access to it at the moment.

Good luck

---

### Post by Jason Pettitt on 2007-06-13
Thanks for replying. Sadly it doesn't seem to make any difference with either kernel. I've done a little testing and discovered I can send very short emails, but nothing longer.

---

