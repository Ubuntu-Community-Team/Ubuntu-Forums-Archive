---
title: "Wireless woes with Atheros AR5212"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by DPic on 2007-09-20
I can't get my laptop to pick up any wireless networks. It has the Atheros AR5212 and i believe i had it working fine before. I am running Feisty 32-bit and since i reinstalled it, my wireless has not been functioning. I tried re-installing Ubuntu multiple times and i don't think i got wireless to work using the LiveCD either. My friend has the same thing but it works fine for him. Anybody have any idea how to fix this problem?

---

### Post by Paris Heng on 2007-09-21
> **DPic said:**
> I can't get my laptop to pick up any wireless networks. It has the Atheros AR5212 and i believe i had it working fine before. I am running Feisty 32-bit and since i reinstalled it, my wireless has not been functioning. I tried re-installing Ubuntu multiple times and i don't think i got wireless to work using the LiveCD either. My friend has the same thing but it works fine for him. Anybody have any idea how to fix this problem?

Hi, what are your 5212 type? **PCMCIA or PCI or mini PCI?**
Regards

---

### Post by DPic on 2007-09-25
How can i tell? Is there a terminal command? It's on my laptop.

---

### Post by Paris Heng on 2007-10-03
> **DPic said:**
> How can i tell? Is there a terminal command? It's on my laptop.

What type of Wifi NIC that you used? That the matters.

---

### Post by Lambert on 2007-10-03
> **DPic said:**
> I can't get my laptop to pick up any wireless networks. It has the Atheros AR5212 and i believe i had it working fine before. I am running Feisty 32-bit and since i reinstalled it, my wireless has not been functioning. I tried re-installing Ubuntu multiple times and i don't think i got wireless to work using the LiveCD either. My friend has the same thing but it works fine for him. Anybody have any idea how to fix this problem?

When it was working before, do you remember installing linux-resticted-modules? atheros uses the madiwifi driver package which I don't believe is installed by default. It is part of the linux-restricted package.

---

