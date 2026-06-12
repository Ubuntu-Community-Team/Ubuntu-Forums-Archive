---
title: "Trying to  use Techkey Bluetooth 5.0 dongle"
date: 2021-08-22
forum: Networking &amp; Wireless
---

### Post by mariofanboy-21 on 2021-08-22
Good day everyone, since I've managed to get myself a Bluetooth 5.0 dongle from Techkey, I have been dealing with tons of issues installing the thing even after following the rules an Amazon review gave to to get itto work on Linux, I have been still suffering from issues to getting it to work. What can I do to fix this issue

Link to the review on Amazon that explains how to operate on Linux 
[https://www.amazon.com/portal/customer-reviews/mobile-media-feed/B085LB5Y8M/ref=cm_cr_dp_mb_crsl_img_0?ie=UTF8&physicalId=51vOBm5pD4L&imageExtension=jpg&reviewId=R2FUH27BNFZTIF](https://www.amazon.com/portal/customer-reviews/mobile-media-feed/B085LB5Y8M/ref=cm_cr_dp_mb_crsl_img_0?ie=UTF8&physicalId=51vOBm5pD4L&imageExtension=jpg&reviewId=R2FUH27BNFZTIF)

---

### Post by praseodym on 2021-08-24
Please plug it in and run
```

lsusb
lsmod
usb-devices
hciconfig --all
```

---

