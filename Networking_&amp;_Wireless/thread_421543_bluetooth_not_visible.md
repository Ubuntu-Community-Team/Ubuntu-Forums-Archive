---
title: "bluetooth not visible"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jamaas on 2007-04-24
I can send files from my dell notebook running edgy to my phone but the computer is not visible to the phone to accomplish any pairing.  Any suggestions about why this might be and/or how to fix it?

Thanks

Jim

---

### Post by bnuytten on 2007-04-24
man hcid.conf -> look for the discovto option near the end
fire up your favorite editor and change it in /etc/bluetooth/hcid.conf
/etc/init.d/bluetooth restart

---

### Post by jamaas on 2007-04-24
Thanks for this, checked the value of discovto and it is set to 0 which means that bt should be discoverable continuously, with no stop time.  Any other suggestions?

Thanks

Jim

> **bnuytten said:**
> man hcid.conf -> look for the discovto option near the end
fire up your favorite editor and change it in /etc/bluetooth/hcid.conf
/etc/init.d/bluetooth restart

---

### Post by bnuytten on 2007-04-26
> **jamaas said:**
> Thanks for this, checked the value of discovto and it is set to 0 which means that bt should be discoverable continuously, with no stop time.  Any other suggestions?

Correct. You should now be able to "see" your Ubuntu box with your cell phone. To succesfully pair the device you need to configure the PIN and *I think* the PIN helper too. Below is my configuration: /etc/bluetooth/hcid.conf:
```

options {
        autoinit yes;
        security auto;
        pairing multi;
        passkey "1234";
        pin_helper /usr/bin/bluez-pin;
}
device {
        name %h;
        class 0x3e0100;
        iscan enable; pscan enable;
        discovto 0;
        lm accept, master;
        lp rswitch,hold,sniff,park;
}

```

---

