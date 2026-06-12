---
title: "internet connetion problem"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by Hasan55 on 2014-02-01
hey guys help me plz......................



when i conneting to the internet at the fast time then no problem happning...but if i disconnet internet connetion for SOMETIMES without unplauge THE MODEM AND AGIN TRY TO RECONNET TO THE INTERNET THEN A MASSEGE IS COMMING ON MY SCREEN..........& not getting connetion till unplauge the modem . HOW DO I SLOVE MY PROBLEM........




here is my problem screen shot
...............................

---

### Post by varunendra on 2014-02-02
Is it a Wireless (WiFi) dongle or a CDMA/3g/4g modem?

Please show us the output of -
```
lsusb
```
when it is plugged in.

**PS:**
If it is a 3g modem, it is normal for it to not be able to connect without resetting it completely, which means a power-cycle, which further means an unplug-replug cycle with a suitable (10-30 seconds) gap in-between.

This is due to the way these devices work, and the frequency of the problem is usually dependent on the quality of service you are getting from your ISP. For example, I need to do this 4-5 times an hour when I use Tata Docomo, while usually just once or twice when using Airtel or Vodafone. The quality of service may be dependent on the area you are in, signal reception quality, as well as the quality of your service provider (how honest/efficient or how crappy they are).

---

### Post by howefield on 2014-02-02
Thread moved to the "*Networking & Wireless*" forum.

---

