---
title: "openvpn client setup"
date: 2023-01-18
forum: Networking &amp; Wireless
---

### Post by gian on 2023-01-18
Ok, so I prepared a RW connection on Ipfire 2.27.172, dowloaded the files .ovpn, .key, .p12 to my laptop running Ubuntu 22.04, and tested the connection with:
sudo openvpn --client --config /etc/openvpn/client/desktopclient.ovpn
The result messages ended with Initialization Sequence Completed.
I was able to ping my remote hosts, but wasn’t able to load the html pages from them, i.e. the empty screen kept waiting forever to load the page.
What am I missing …?
Thanks for reading,
-GianLuca

---

