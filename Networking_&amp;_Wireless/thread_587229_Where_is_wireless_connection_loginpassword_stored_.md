---
title: "Where is wireless connection login/password stored in Gutsy?"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by ormandj on 2007-10-22
I looked in keyring manager, and I don't see anything, but somehow my wireless username/password got stored on one of the public console laptops. Where do I find this information so I can delete it? I don't want anybody logged into the machine to be able to use my wireless credentials to get online.

Second question, is there any way to make network-manager user-specific? So I can login to a wireless network under my user account, but when I logoff it drops, and nobody else will have access to the information?

Thanks!
David

---

### Post by ormandj on 2007-10-23
Sorry to bump my own thread, but this is important. Thanks.

---

### Post by FoxOne on 2007-12-06
bump

---

### Post by James Paige on 2007-12-06
there is a hidden folder inside your home directory called **.gnome2** and inside that is a folder called **keyrings**

I recommend caution when deleting them (I just moved mine to a backup directory when I wanted to test resetting them)

---

