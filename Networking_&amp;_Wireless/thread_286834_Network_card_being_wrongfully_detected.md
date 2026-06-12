---
title: "Network card being wrongfully detected"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Abild on 2006-10-28
Hi

I've just installed Edgy on my brothers computer. Everything works fine except the network card. The problem is that it's being wrongfully detected. The network card in the machine is a Realtek RTL8201CL witch is integrated on his ASRock 939S56-M motherboard. The network card is detected as a SiS 190 gigabit network adapter and the module being loaded for it is sis190.
The network card works with this module, but the network is literally crawling. Transfer speeds averages at about 200 B/s (yes, thats Bytes). I can ping other machines on the network normally.

I install all my computers over LAN with network boot. The funny ting is that during install the network card was correctly detected and worked normally.

Can anyone tell me which module i should use for the RTL8201CL chip and how to get it loaded during boot instead of the sis190 module?

UPDATE:
I think maybe the network card isn't being wrongfully detected after all. I tried running the installer to see which module it loads for the network card. I found out that it also loads the sis190 module. For some reason it works fine during setup but it stops working once the system has been installed.

UPDATE2:
I did a reinstall and now the problem seems to have disappeared. I still don't know what caused it though.

---

