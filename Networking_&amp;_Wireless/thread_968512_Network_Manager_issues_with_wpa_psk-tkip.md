---
title: "Network Manager issues with wpa psk-tkip"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Dakani on 2008-11-02
I'm currently running Ubuntu 8.10 and I cannot get the new Network Manager to connect to my hidden wireless network. 

In Hardy, I was able to connect before using the updated community broadcom drivers, I did not have to manually go through ndiswrapper or fwcutter. Now in Intrepid, I do believe it is using the same driver and the wireless appears to be working as Network Manager can scan for networks and provide a list.

But every time I try to connect to my hidden wireless network, which uses wpa psk-tkip, it attempts to authenticate but fails and asks for the passkey again.

I really do not like how Network Manager bundled wpa and wpa2 as well as choosing it as automatic. I would rather specify what to use and everything.

I attempted to use wicd, but that didn't work out either. And I really don't think it is a hardware issue because it was running perfectly on Hardy with the community-based drivers.

Any help on this is appreciated.

EDIT:
OK, I know for sure that it has to be Network Manager because I have just tried and successfully connected to my university's wireless network that uses wpa/wpa2 enterprise, TTLS, CA cert, with inner authentication PAP.

If it can do wpa/wpa2 enterprise, which is more complex, why can it not do wpa/wpa2 personal correctly?

---

### Post by Ludachrispeed on 2008-11-05
Sorry not to answer your question but... How were you able to connect to a WPA2 Enterprise network?  I'm having a lot of trouble with this after the upgrade.

There are a bunch of people venting about this in another thread: [http://ubuntuforums.org/showthread.php?t=970236](http://ubuntuforums.org/showthread.php?t=970236)

If your method wasn't insanely complicated, maybe you could help out :p

---

