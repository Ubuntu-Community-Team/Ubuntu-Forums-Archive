---
title: "driver needed"
date: 2018-08-07
forum: Networking &amp; Wireless
---

### Post by ravensm on 2018-08-07
i am running ubuntu gamepack 16.04 with kernel 4.15

[https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1533685053&sr=8-1&keywords=tl-wn722n](https://www.amazon.ca/TP-Link-TL-WN722N-Wireless-Adapter-Detachable/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1533685053&sr=8-1&keywords=tl-wn722n)

the drivers i have been able to find state v2 but the questions asked in amazon says that model is v1...does anyone know of a driver what works for my kernel?

---

### Post by ravensm on 2018-08-07
[https://github.com/abhijeet2096/TL-WN722N-V2/tree/kernel4.15](https://github.com/abhijeet2096/TL-WN722N-V2/tree/kernel4.15)

this is the driver for v2

---

### Post by chili555 on 2018-08-07
Let's find out. Please insert the device and run and post the result of the terminal command:```
lsusb
```If it is v.1, I think you'd know it because the device would start to work immediately, just like mine does!

---

### Post by ravensm on 2018-08-07
thats the problem, i havent bought it yet, im trying to find out if anyone knows of a driver for v1 just incase it is indead v1 and not v2. the only driver ive been able to findfor kernel 4.15 is v2

---

### Post by jeremy31 on 2018-08-08
V1 has a module that is included in the kernel ath9k_htc, you plug them in and use them without installing anything

---

### Post by ravensm on 2018-08-08
sswwweeeettttttt, so in other words, whether or not its v1 or 2 i will be ok, nice!!!

---

### Post by chili555 on 2018-08-08
If it is v.1, it will work with no further action on your part. If it is v.2, you will have to compile a driver, probably the one you linked above.

---

### Post by ravensm on 2018-08-08
thats awesome, ive been using windows solely since i was a kid, and im in my 30's. but i just switched over to linux and its a huge leap. anyways, i guess my question is answered, thanks

---

### Post by chili555 on 2018-08-08
It is big leap, indeed. I think you will find the community here patient and helpful. Post back if we can assist you further.

---

