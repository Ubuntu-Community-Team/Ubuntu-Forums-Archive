---
title: "eth1,eth2 - eth20 HELP!"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by wildseven on 2008-02-27
I don't understand why my eth keeps going up! i don't understand. please help me. This is happening on a wired connection and i am using an HP dv6636nr

---

### Post by tommohawk on 2008-02-27
You think that's weird!!

My wireless connection is now called wlan0_rename ......????!!!!!

Don't know where that came from!

---

### Post by wildseven on 2008-02-27
i see many people have the same problem. I saw a fix for this a while back, but i never payed attention to it and now i can't find it. It has something to do with mac address i think. I changed mine and my eth number still changes!

---

### Post by spd106 on 2008-02-27
It sounds like udev is having troubles and I've no idea how to reset it.

Can you set the interface name in the /etc/iftab? Just add the mac address of your interface as per the example in the iftab man page.

---

### Post by wildseven on 2008-02-28
i don't have an iftab. am i supposed to?

---

### Post by wildseven on 2008-02-28
i fixed it! woo!

---

### Post by in_flu_ence on 2008-03-21
How did you fix that problem?? Wildseven?

---

