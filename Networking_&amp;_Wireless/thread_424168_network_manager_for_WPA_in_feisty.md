---
title: "network manager for WPA in feisty?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by feydrutha on 2007-04-26
I am trying to get connected to my access point which has WPA encryption enabled (with a newly installed feisty)..

I've seen the big thread on this issue ([_here_]("http://ubuntuforums.org/showthread.php?t=202834")), which talks about manually writing stuff in /etc/network/interfaces file. It also says network manager applet should be disabled.

Before I try that out, I would like to understand: does network manager have no support at all for wpa? The reason I ask is that [this]("http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html") article seems to explain how to get wpa working with the network manager.

Here is a screenshot from that article:

[IMG]http://www.debianadmin.com/images/wpa/4.png[/IMG]

...where we can see there is a WPA option in the network manager applet.
When I try that myself, however, there is no WPA option. Anyone know what I can do to make it appear? The article is about ubuntu edgy, whereas I am using feisty, so there may be some difference....

---

### Post by jhpope on 2007-04-26
prob using a different driver that supports wpa

---

### Post by feydrutha on 2007-04-26
I have an acx 111 chipset, and the acx module is loaded.

As far as I can see, it doesn't seem to be in the [list of drivers supported by wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/"). 

So should I try ndiswrapper instead? 

Or just give up on the network-manager and configure my /etc/network/interfaces instead? would I still need wpa_supplicant to do that?

---

### Post by jhpope on 2007-04-26
past knowing that your chipset is not supported i have no idea. it seems like if you  manual configure you get better results, no idea why. i'm a n00b having trouble with my rt61 chipset so all i could say is to try and search here in the forums or check google.

---

### Post by k1001001 on 2007-04-26
I have an RT2500 wireless card and am also in the same position when using the Feisty live CD. If you get it to work, please tell me how. I will not switch to Feisty until I have this issue resolved.

---

### Post by erm67 on 2007-04-28
> **k1001001 said:**
> I have an RT2500 wireless card and am also in the same position when using the Feisty live CD. If you get it to work, please tell me how. I will not switch to Feisty until I have this issue resolved.

I have a rt2500 card in feisty and it works.
Feisty ships with the old driver without wext so it is not supported by wpa_supplicant or the other ubuntu utilities. The old method should work or use the RaConfig2500 utility from universe putting a line with ra0 in /etc/rtx000.conf.
The new driver that supports wext is being developed slowly and is still buggy, as far as I know only suse  ships a cvs version of it, but it did not work very well the last time I checked it.
or copy /etc/Wireless/RT2500STA/RT2500STA.dat from a working installation

---

### Post by k1001001 on 2007-04-30
> **erm67 said:**
> I have a rt2500 card in feisty and it works.
Feisty ships with the old driver without wext so it is not supported by wpa_supplicant or the other ubuntu utilities. The old method should work or use the RaConfig2500 utility from universe putting a line with ra0 in /etc/rtx000.conf.
The new driver that supports wext is being developed slowly and is still buggy, as far as I know only suse  ships a cvs version of it, but it did not work very well the last time I checked it.
or copy /etc/Wireless/RT2500STA/RT2500STA.dat from a working installation
That's pretty much what I'm doing now. I guess there's not really much reason to switch to Feisty then. I was hoping that wireless would be improved.

---

### Post by erm67 on 2007-04-30
> **k1001001 said:**
> That's pretty much what I'm doing now. I guess there's not really much reason to switch to Feisty then. I was hoping that wireless would be improved.

After the workaround is working very well, rt2500 is not improved but not regressed.

---

