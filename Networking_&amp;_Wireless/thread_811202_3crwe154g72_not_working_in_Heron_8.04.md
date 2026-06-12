---
title: "3crwe154g72 not working in Heron 8.04"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by decrease789 on 2008-05-28
I have tried to use 3coms 3crwe154g72 (rev 01) wireless pcmcia card on heron and I can not get it to work.

I tried using ndiswrapper to no avail (not even the link light only comes   on occasionally) and with prism54pci (link light is constant and activity light flashes quickly). Is anyone else have problems with this? Any suggestions? Kernel 2.6.26-17 

Cheers
James

---

### Post by verdigris on 2008-09-06
When I did a fresh install of Hardy on my laptop (which previously had Gutsy, but couldn't upgrade), I was surprised that the card was recognised without even having to bring up ndiswrapper. It was working fine except with encrypted networks. I had to install an older distro, made sure that the card was working, then *upgrade* (not install) to Hardy. Now it's working fine (though I'm not sure which rev my card is).

---

