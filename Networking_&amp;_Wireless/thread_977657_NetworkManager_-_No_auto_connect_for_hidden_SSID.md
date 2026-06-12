---
title: "NetworkManager - No auto connect for hidden SSID"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Beliar on 2008-11-10
Hi everybody,
I have a problem with my Wireless LAN. In the former Ubuntu releases, NM would connect my WLAN automatically on start-up. Its a WLAN with private WPA encryption and hidden SSID. 

But since I installed (not upgraded) Intrepid Ibex, it doesn't connect at start. The WLAN's profile is still stored. I just have to click "Connect with hidden WLAN" -> pick my Network. In its profile, the option "auto connect" is checked.

Its very annoying and Pidgin seems not to support dbus, because I have to connect my profiles manually, once I got my connection back. Same for some other programs that would like to have internet connection before they start.

Btw. a Problem that I had before is, that NM would try to connect to my Network and kind of "hang". The left dot (I guess for client) is always glowing, the other one not. After a time, it says "unable to connect". If I check iwconfig etc, it seems to connect to the AP, but it doesn't get an IP. 
Restarting /etc/init.d/networking, logging off and on again, deactivating nm-applet or killing it and restarting, does not work. It will also ask me for the password over and over again.
But when I restart (kinda windows style), it works perfectly again. 
That doesn't happen so often, its annoying, but I never started a Thread about it or found a solution. But since I'm already posting, maybe somebody has the same problem. 

Issue no1 though appears on EVERY start.

Thanks for any advice, reply, what ever :)
cheers,
Beliar

---

### Post by dalyx on 2008-12-02
I also have this problem with a fresh install of Ibex. I have to manually connect to hidden SSID every time I log on, suspend or something similar, even though the settings of Network Manager are at "auto connect". I found that a bug was open regarding this problem, but it looks like it is still there.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273467](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273467)

---

