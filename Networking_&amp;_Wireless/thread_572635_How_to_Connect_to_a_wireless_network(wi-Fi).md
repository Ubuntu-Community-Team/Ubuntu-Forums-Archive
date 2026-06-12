---
title: "How to Connect to a wireless network(wi-Fi)"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by young_mafia on 2007-10-10
I have a Gateway MX6640 

with windows i connects automatically


with ubuntu i am not to sure

so please tell me the steps to connecting

---

### Post by Lambert on 2007-10-11
> **young_mafia said:**
> I have a Gateway MX6640 

with windows i connects automatically


with ubuntu i am not to sure

so please tell me the steps to connecting

Depending on the wireless device in your PC, a driver might load automatically or you might have to do some configuring.

To start simply open up network from System->_____ ->network (sorry, drawing a blank and can't remember what the next menu is, just mouse over and look for the next drop down to show network)

Do you see a wireless device listed here? If so just configure it from there.

If you don't see a wireless device then from the top panel, click on applications->accesories->terminal

type this in that window

```

sudo lshw -C network

```

And the device is an internal wireless card correct?

---

