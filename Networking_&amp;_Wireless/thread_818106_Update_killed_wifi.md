---
title: "Update killed wifi"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Bishop Hill on 2008-06-04
I'm using an EEE 900 with Xubuntu 8.04, and there was some updates this morning that I had to install. After that, the system rebooted, and when everything came online, the wireless was dead.

What should I do:confused:?

(and yes, I understand that this is not very informative, but I dont know where to find more info:/)

---

### Post by wdaniels on 2008-06-04
There was a kernel update today, so you will need to repeat the steps to compile and install the patched madwifi drivers for the Eee's atheros card, since it is not supported by the default Ubuntu set. You will have to do this after every kernel update until the card is properly supported (and also for the acpi module if you are using that). Fortunately, kernel updates don't happen all that often.

It's probably best to follow the same set of instructions that you used originally if you can, otherwise refer to the community documentation for the Eee PC [here]("https://help.ubuntu.com/community/EeePC").

---

### Post by wdaniels on 2008-06-04
Oh, sorry, I see you're using the new 900 one, I was talking about the older model - I don't know whether they're the same or not for the wireless hardware.

---

### Post by Bishop Hill on 2008-06-04
Worked like a charm.

Thanks!

---

### Post by Cavalryman on 2008-06-10
So, I did everything on the link above. I tried changing the driver as directed, and then I tried using the ndis wrapper. I got exactly no response with either of them. Is there anything else I can do, or am I just hosed?

---

