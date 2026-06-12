---
title: "new kernel might have killed my wireless"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by fawilson31 on 2008-05-27
Latest Kernel update might have killed me wireless.

Hello all. The other day I allowed Hardy to apply automatic upgrades. As part of the upgrade it went to kernel 2.6.22.18, after that the wireless was no longer able to connect to the router/AP.

I rebooted to kernel 2.6.22.14 generic and I have been able to log into the wireless.

I am using WPA2 Personal with TKIP on channel 8 (also tried channel5). Using NDISWRAPPER With a broadcom wireless AirForce adapter.

I tried to manual configure the setting with a static IP with no luck.

The only thing that seems to work consistently is booting in a past kernel.

I am somewhat of a noob so if you need specific screenshots or logs you may have to give me details how to get them here.

Thanks,
Fred

---

### Post by fawilson31 on 2008-05-27
OH YEA, I am using NDISWRAPPER

---

### Post by shaggy1054 on 2008-05-27
I'm having the same problem; in my case, the kernel update made my wirless degrade following a reboot until it stops. My connectivity has also gone to ****. I'd like to test the rebooting in the old kernel but I have no idea how to do so - help a brotha out if you would?


In case it matters, I'm using the madwifi for an atheros wireless card.

---

### Post by Promaster91 on 2008-05-27
Did you try reinstalling the drivers or NDISWRAPPER? I also had to do that because of the kernel update.

---

### Post by shaggy1054 on 2008-05-27
I reinstalled the madwifi driver. Is there something else I should try and reinstall?

---

### Post by shaggy1054 on 2008-05-28
Having figured out how to reboot in an earlier kernel (.16 as opposed to .18), it appears as if things are working now. Weird...

---

### Post by fawilson31 on 2008-05-28
I have not tried that. Honestly never thought of it. Can you explain why this may or should work?

The adapter is available and it can see the wireless router/AP it just will not connect.

Thanks,
Fred

> **Promaster91 said:**
> Did you try reinstalling the drivers or NDISWRAPPER? I also had to do that because of the kernel update.

---

