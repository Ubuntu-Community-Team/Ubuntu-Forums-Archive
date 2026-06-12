---
title: "realtek 8201cl not recognized"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by eolo999 on 2005-09-22
hi guys.
My realtek 8201cl is not recognized by "discover"...
i know that rtl 8201cl is a phy card (not understood exactly) and it need a "MAC" to control it which is differentv from motherboard to mb. My mb is an asrock k8 upgrade-nf3 and I can't figure out which is the MAC chip....
ok i'm very confused, someone can help me???? ](*,)

---

### Post by mlomker on 2005-09-22
My laptop has a similar card, but the sis900 driver loads and works fine.

Try this:

```

sudo modprobe sis900

```

Post the output of **dmesg | tail** and **ifconfig** after doing that.

---

### Post by FloSynergy on 2007-06-19
hey there,

did you manage to resolve this issue? If so, I'd love to know how, since it seems that i am struggling with a similar issue - check it out here.

I'm looking forward to hearing from you,

be well,

flo

---

