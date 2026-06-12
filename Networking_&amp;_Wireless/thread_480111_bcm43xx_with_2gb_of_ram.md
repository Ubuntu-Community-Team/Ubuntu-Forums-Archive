---
title: "bcm43xx with 2gb of ram"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by PPower on 2007-06-21
Apparently there are issues with the bcm43xx driver and 2GB of RAM. These were apparently fixed in 2.6.21, but Feisty runs 2.6.20, which has 2 fixes:
 
In .20:
 
    [PATCH] bcm43xx-softmac: Fix system hang for x86-64 with >1GB RAM
    [PATCH] bcm43xx: >1G and 64bit DMA support
 
But in .21:
 
    [PATCH] bcm43xx: Fix problem with >1 GB RAM 
Does anyone know if it will work on my system with 2GB of RAM? Im not sure as the bug appears to have been fixed twice. Are these fixes backported?

---

