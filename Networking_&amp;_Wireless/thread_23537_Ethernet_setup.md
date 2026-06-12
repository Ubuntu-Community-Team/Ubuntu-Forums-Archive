---
title: "Ethernet setup"
date: 2005-04-02
forum: Networking &amp; Wireless
---

### Post by mcgodx on 2005-04-02
Last night, I had Ubuntu, and it was working fine, and i could go on the internet, etc.

Now, I can't.  I'm not sure how to get it working.  I configured the ethernet in the Network-admin, but it never stays active.  Thank you much.

---

### Post by soul_rebel on 2005-04-03
Tell us about the card: model a and manufacturer

then post the output of 
ifconfig
dmesg (just relevant part, look for eth0 or the card driver)

than try
ifup eth0
and post any error.

perhaps post also a
lsmod

Nobody can help without info, there are so much people asking help that post like yours usually are ignored...

bye

---

