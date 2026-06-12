---
title: "Ubuntu Wireless barley connects and is very slow."
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by l-combs on 2014-06-15
So, I have been using Ubuntu as my primary operating system for about 1.5 years now. Every thing has been great until yesterday. I booted Ubuntu, and it wouldn't connect to wireless(My phone and other devices were fine). After messing with it for about a day now, it finally connected and has been very slow ever since. To be specific my download speed is about 16mb/s and Ubuntu has barley been getting 0.5mb/s.

I was wondering if maybe I could re-install my wireless drivers. I'm not sure what to do,


God Bless & Thanks,


Lucas

---

### Post by squakie on 2014-06-15
What brand/model, etc., of adapter (lsusb if it's a usb dongle, lspci if it's built it)?

---

### Post by l-combs on 2014-06-15
It's Built In, I'm not too sure

---

### Post by squakie on 2014-06-16
Open a terminal window (ctrl/alt/F1) and log in using your normal userid and password.  The password is not echoed to the screen so it doesn't look like anything is happening as you type it, but it is.  Press enter at the end of each.

Now type:

lspci | grep Network <press enter>

Post back the output here in a reply.

---

