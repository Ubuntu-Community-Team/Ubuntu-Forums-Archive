---
title: "Mediatek MT7630E driver"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by jahidul hamid on 2014-06-22
ubuntu claims that this driver is supported, But it's not. can i know when will this device be supported, and on which version?

---

### Post by Vladlenin5000 on 2014-06-22
Where exactly have you read that?

---

### Post by jahidul hamid on 2014-06-22
[http://www.ubuntu.com/certification/catalog/component/pci/14c3%3A7630/](http://www.ubuntu.com/certification/catalog/component/pci/14c3%3A7630/)

---

### Post by Vladlenin5000 on 2014-06-22
Nevermind...

There's no solution yet apparently. There are some notebooks with Ubuntu preinstalled with some driver that works but not present in main repositories / not included in installation media.

---

### Post by jahidul hamid on 2014-06-22
yeah, i just installed kernel 3.16.0 rc2. even that kernel doesn't include the driver. may be utopic too will not support this device.

---

### Post by marko12 on 2014-06-29
I found this yesterday [http://www.mediatek.com/en/downloads/mt7630-pcie/](http://www.mediatek.com/en/downloads/mt7630-pcie/) but I don't know how to install it because I'm newbie in Ubuntu. Can someone test this and tell if it works? Sorry for my English

---

### Post by gmoutso on 2015-04-01
try the instructions at [https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e)

---

### Post by Paolo_Mascellani on 2015-10-17
> **gmoutso said:**
> try the instructions at [https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e)

Great! This worked fine for me (ASUS X554L with Ubuntu 14.04.3).

The command:
    git clone [email]git@github.com:kuba-moo/mt7630e.gitgit[/email] clone [email]git@github.com:kuba-moo/mt7630e.git[/email]

gave me:
    Permission denied (publickey).

But I downloaded the zip from the provided github url instead.

Thanks very much.

---

