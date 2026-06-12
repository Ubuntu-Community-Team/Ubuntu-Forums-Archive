---
title: "BCM4306 mysteriousy stopped working?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by rkrizan on 2008-11-24
Today, for some reason, I returned to my computer to find that my network connection was down. First I thought it was my router, no, that wasn't it, then I thought maybe I had wireless networking disabed (somehow) - nope.

Then I grabbed my Atheros slot card, popped it into my laptop, and it found my wireless network without any issues. I did a hardware scan, and it still shows up, but I can't get it to find my wireless network _at all_. It was working fine until today.

Anyone have any suggestions to help me resolve this issue?

Thanks.

---

### Post by Olivier2371 on 2008-11-24
I there,

I did the same thing early this evening, My laptop wireless works fine, but I wanted to test an old pc card I had(WPC11 rev.3) which work perfectly with WEP settings. 

Then I removed the pc card but my wireless adapter (Broadcom 4311) wouldn't work. So I rebooted the sytem And everything was back to normal.

---

### Post by Ayuthia on 2008-11-24
If you go into the Terminal, what does lshw -C network show?  Your wireless card should appear as one of the results and if all is well, it should not show UNCLAIMED or DISABLED.

---

