---
title: "WPA1 and ndiswrapper"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by m_vitaly on 2008-06-02
I have a strange situation.
And I hope you will help me.

Router: D-Link DI-524
Wifi: D-Link DWL-G122 (USB) Rev: D1
Module: ndiswrapper (comes on ubuntu 8.04 cd)
Driver: the version from the D-Link web site for rev D1 and for WinXP

All my configuration is ok (hope so).
But what happens is like that:
I can't connect to my router with WPA1 key. When i run iwevent I see that it gets the network ok and after 1 second it says that I'm not connected to it and it repeats again and again.

I was able to connect once. And I'm able to connect to any network without WPA or WEP. But I can't connect to my network.

I think it could be one of these problems:
1. My WPA passphrase it too long (not sure about that because they are encoded into fixed length bytes)
2. Some other process is initiating the reconnect
3. This is normal behaviour when WPA key is wrong (unlikely but maybe ubuntu thinks it is)
4. Some sort of power saving on USB feature (even when it's not a laptop? anyway already tried to play with bios settings)
5. USB Wifi model specific problem (I can remember the same happening in WinXP with this model - but not sure it was exactly the same problem)

The whole idea of this post is that I couldn't find any info about this particular situation (and search doesn't function right now).

It's not so easy to get to logs and edit files because this is a blank 8.04 install (with ndiswrapper) and with no mouse on the PC :) . For now using vi to edit /etc/networking/interfaces and the like.

I know I should just switch WPA off and try without it, but I have many other PC that will be affected and if it will work I'll leave it unsafe (actually even more unsafe) for good :) .

Hope you'll help me or at least clarify the situation.
Thanks.

---

