---
title: "Network card in docking station not recognized when hot docked."
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by snakyjake on 2007-03-02
**Problem:**
Network card in docking station not automatically recognized when hot docked.  I want to hot dock my laptop and have the network card work without rebooting.

**Situation:**
I dock my laptop (laptop is running) into the docking station with the ethernet network card.  The network card is not automatically recognized.  The network card is recognized only after rebooting.  I want a solution to recognize the network card without having to reboot.

**Troubleshooting:**
1. Rebooting the laptop when docked = success.
2. /etc/init/d/networking restart = fail.
3. ifup eth0 = fail.

Is there another command to recognize the network card without rebooting?

Thank you.

---

### Post by NetMatrix on 2008-06-06
You'll need to reload the module for the network card.

```
modprobe 'your ethernet module'
```

---

