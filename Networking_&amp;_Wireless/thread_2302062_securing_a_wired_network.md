---
title: "securing a wired network?"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by Sandgoose on 2015-11-07
I have a laptop is connected to the router via wifi, I would to share internet through the ethernet port but I would like the only data / routing it does to be encrypted (vpn?) because the other end of the cable (access point connected) is in an insecure location and I want to avoid tampering. (unplugging is fine just not plugging random junk to get full access to my network, MAC filtering is not enough, easy to get around and not even fully supported by the router)

is something like this possible? is there an easier solution I should be looking into, I have never had to run a setup like this before so Im not sure where to even start looking

any advice greatly appreciated.

Thank you

---

### Post by Sandgoose on 2015-11-12
after a little research...

I figure the vpn thing is mainly for tunnelling network traffic over the internet and not encrypting/securing local networks, it wont work as far as I can tell?

 I looked into the (easy to bypass) mac filtering built into 2 routers (and one access point) but routers only seem to support it for the wireless connections and not the wired ones.

for now settled on for now turning off dhcp and manually assigning ip addresses this has worked but is far from a perfect solution.

**tldr** suggest a better solution to stop strangers plugging junk into my rj45s?

(it can not be glued or physically locked else I would have done already ^^)

Thanks

---

### Post by ian-weisser on 2015-11-13
How will your system identify friendly (or suspicious) hardware? Whitelist? Blacklist?

---

