---
title: "Wireless trouble: link is not ready"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by mcbutterbuns on 2007-07-13
My wireless card is a netgear WG511t. It is recognized by my computer. Whenever I try connecting to my wireless using knetworkmanager, it hangs at 26% for a while.

A quick tail through messages shows this error:
ADDRCONF(NETDEV_UP): ath0: link is not ready

I don't believe it to be a WPA problem because I have disabled all encryption on my router (for now) and still cannot connect. I can't connect to any of the wireless signals in the area either.

Any ideas?

---

### Post by mcbutterbuns on 2007-07-13
I figured it out. Seems I needed to do some editing of /etc/network/interfaces

By using the Network Settings control panel, I was able to connect by setting DHCP to auto and setting my essid (I didn't have to set the WEP key)
This added the line: wireless-essid <essid name here> to my interfaces file.
Thats all it took for the wireless without encryption


To enable WPA, i used the resource found here:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Now its working! I just had to enable WPA on my router. BTW, don't ever by a DLink DI-524. I had to hand edit the HTML on the web interface so that the javascript would work and I could post the settings to enable WPA. I need a new router.

---

