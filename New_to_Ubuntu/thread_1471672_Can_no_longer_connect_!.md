---
title: "Can no longer connect !"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Florida-Philly on 2010-05-03
I installed Ubuntu 10.04 as a dual-boot, alongside of Windows 7.
I downloaded and installed Mozilla's Firefox and Thunderbird, and all was well.
I browsed the internet and read several pages here in the forum, being a newbie. By then it was late so I put the computer to sleep and went to bed. Next morning I found that Ubuntoo would not wake up, so to speak. I had to turn off the computer and reboot into Ubuntu. I attempted to go online and it would not connect. I tried to use Email and it would not connect. So I did a restart and went into Windows, clicked on Firefox and had no problem, same with Email...no problems. Can anyone tell me why I can no longer connect in Ubuntu but have no problem connecting in Windows? I hope it's something simple.

---

### Post by -humanaut- on 2010-05-03
Could you log into ubuntu open a terminal type 'ifconfig' and post it back here?

---

### Post by Ibidem on 2010-05-03
Or just see whether Ubuntu can now connect.  Occasionally supend/hibernate will kill wireless; one of  the surest ways to get it working again is reboot into Windows, get it working, and restart in Ubuntu, in my own experience.

---

### Post by Florida-Philly on 2010-05-03
> **-humanaut- said:**
> Could you log into ubuntu open a terminal type 'ifconfig' and post it back here?

I restarted the computer and went to Ubuntu, terminal, and typed ifconfig.
I have included the results below.
I forgot to mention that I'm running a router. But it WAS connecting at first. 
So then I disconnected the router and ran it straight through, after turning everything off for a few minutes then booted into Ubuntu again, and got a slightly different set of numbers, listed:
ifconfig:
link encap: Local Loopback
inet addr: 127.0.0.1  Mask: 255.0.0.0
inet 6 addr: : : 1/28s Scope: Host
up loopback running MTU:16436 Metric:1 
Rx Packets:350 (1st time) errors:0 dropped:0 overuns:0  frame:0
Rx Packets:230 (2nd time)     "        "        "          "
Rx Packets:222 (3rd time)     "        "        "          "
Collisions:0  Txqueuelen:0
Rx bytes: 19512 (19.5kb)   Tx bytes: 19512 (19.5kb)
2nd time: 18648 (18.6kb)

---

### Post by Florida-Philly on 2010-05-03
> **Ibidem said:**
> Or just see whether Ubuntu can now connect.  Occasionally supend/hibernate will kill wireless; one of  the surest ways to get it working again is reboot into Windows, get it working, and restart in Ubuntu, in my own experience.

Yes, I tried that before posting and it didn't help. I've tried everything I can think. Thanks

---

