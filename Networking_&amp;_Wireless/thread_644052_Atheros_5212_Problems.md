---
title: "Atheros 5212 Problems"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by nils234 on 2007-12-18
Hello,

Before I begin, please let me make clear that I am very very new to linux and the solution to my problem is probably kind of simple,

I bought a TEW-443PI some days back because it's said to work "Out of the box". I put the pci card on my motherboard and installed a fresh ubuntu gutsy gibbon. Well, the first thing I notice is: It doesn't work out of the box ;). I open the network management but it only gives me options to connect to wired or dial-up networks. So I look a bit further, and I see linux has loaded a "restricted" driver for me, called atheros hardware abstraction layer ( or something in that fashion, you guys probably know what I'm talking about ). After a bit of searching around in the nets I execute "lspci" in the terminal, and I see that it does infact recognise my card like it should. Something like atheros 5212 chipset based network nic. Hardware information shows the same. 

I then executed "iwconfig" but it only shows a "l0 and an eth0". I searched the nets some more, and found out about the madwifi project. Downloaded compiled and installed, all went fine. Followed their instructions, did the modprobe something command. But it doesn't appear to have any effect.

Whitch of you experts can take me one step further? I have googled for houres but can't seem to find any solution :(

Thanks in advance,

Nils Kuijpers
Holland

---

### Post by nils234 on 2007-12-18
By now I've also tried by the ndiswrapper approach. At first I did not want to do this, because I kind of want to leave everything behind that has anything to do with windows, but ok :P Installation and configuration of ndiswrapper went fine, loaded the driver and that went fine. rebooted, but wireless still isn't an option at the network management :(. Also the output of iwconfig still only shows eth0 and l0, no ath0 like it should. lspci and hardware info output hasn't changed.

Please help a poor unix n00b who's realy doing his best to get rid off windows :)

---

