---
title: "How to enter multiple WEP keys in Wireless Assistant"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by skapoor101 on 2007-05-08
Hello all:

I have configured my Netgear router (using 128 bit WEP) to use 4 keys.
My router allows me to set up 4 different keys.

While configuring Wireless Assistant 0.5.5 in KDE I can only specify 1 key as the GUI only has 1 text box for entering the WEP key.  I tried separating the 4 keys by a space but that does not work.

If I change my router's AP to have all 4 keys be the same then it does work but I was wondering how I can get the 4 different WEP keys entered. 

Anyone run into this and has a solution?

Thanks:

-Sam

---

### Post by NilsE on 2007-05-08
The reason it works when you make all four the same is because it really only needs to receive one of the keys not all 4.  If you send it one key it should always try to resove to the first then the second etc until it finds one it likes.

---

### Post by stchman on 2007-05-08
> **skapoor101 said:**
> Hello all:

I have configured my Netgear router (using 128 bit WEP) to use 4 keys.
My router allows me to set up 4 different keys.

While configuring Wireless Assistant 0.5.5 in KDE I can only specify 1 key as the GUI only has 1 text box for entering the WEP key.  I tried separating the 4 keys by a space but that does not work.

If I change my router's AP to have all 4 keys be the same then it does work but I was wondering how I can get the 4 different WEP keys entered. 

Anyone run into this and has a solution?

Thanks:

-Sam

WEP is too insecure, use WPA or WPA2.  WEP is too easily hacked by programs like airsnort or others.

---

