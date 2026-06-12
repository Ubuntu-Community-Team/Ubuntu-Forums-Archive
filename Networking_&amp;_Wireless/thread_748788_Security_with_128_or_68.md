---
title: "Security with 128 or 68"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by abbasali31 on 2008-04-07
I installed Ubuntu 7.10 on my Dell Laptop and is working great except my wireless card with WEP enabled.

It connects fine with my linksys wirless router if WEP is disabled.  I enabled WEP with 128bit security, and went back to my Ubuntu Network Tools option where you could enable WEP as well, but ubuntu wouldn't take Hex character more that what is required.  At certain point it wouldn't accept hex entries.  I then tried 64 bit security, but then ubuntu was unable to make connection.  

Am I missing something.

Regards,

---

### Post by insineratehymn on 2008-04-07
I believe there are two kinds; 128-hexcode and 128-passphrase.

Tried both?

---

### Post by abbasali31 on 2008-04-07
Yeap,  I tried passphrase as well.  Meaning whatever ASCII I used in Linksys to generate the key, I used the same ASCII in ubuntu, but then no luck.  It wouldn't connect to the wirless router.

---

### Post by prshah on 2008-04-07
> **azhar-teza said:**
> but ubuntu wouldn't take Hex character more that what is required.  At certain point it wouldn't accept hex entries.  I then tried 64 bit security, but then ubuntu was unable to make connection.  

In my wireless router (no-name brand), if I am specifying a hex key, I have to precede it with a "0x". I don't know if it is applicable to yours, but if you are preceding the hex key it with "0x" in your router, you should NOT put the "0x" in your ubuntu box when entering the WEP key.

---

