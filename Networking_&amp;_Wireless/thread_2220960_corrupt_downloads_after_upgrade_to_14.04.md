---
title: "corrupt downloads after upgrade to 14.04"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by DLGandalf on 2014-04-30
Hi, 

I've upgraded to 14.04, but it's the upgrade from hell, nvidia drivers seem to crash randomly when opengl is used (read: always with unity) - an more importantly, the network is borked, downloading anything substantial gives corrupt downloads. Even something like rsync/scp which do some validation on protocol level error out with 'corrupt packet' warnings. 

Its a MCP77 nvidia network card, which is driven by the 'forcedeth' driver.
`00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)` 

Has anyone experienced the same problems?

---

