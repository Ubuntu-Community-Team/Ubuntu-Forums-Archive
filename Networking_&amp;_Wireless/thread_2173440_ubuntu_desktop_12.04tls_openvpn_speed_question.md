---
title: "ubuntu desktop 12.04tls openvpn speed question"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by bronzemaxell on 2013-09-09
Hi
I've installed and configured openvpn on dell vostro 360 all in one with intel i3 cpu, and dell vostro 420 desktop with intel i5 cpu,
openvpn bridge mode setup and connectivity all fine, 
when i ftp or http download from server to client, according to firefox and gnome-system-monitor, i am getting about 1m byte/sec  to 1.3mbyte/sec when transfering a 150mB file
my ubuntu desktop openvpn server side has verizon fios 35/35mbps, and ubuntu desktop openvpn client has comcast 50/10mbps
i did speed test on fios and confirmed the download and upload speed is 35/35mbps using [www.speedtest.net]("http://www.speedtest.net").
i've tried cipher none and cipher bf-cbc, and no significant difference in throughput.
both dell cpu load are around 10 to 20%
if i start download multiple files across the openvpn at once, each instance of downloading is still 1mbyte/sec
for example, if i download 3 big files simultaneously, i would see 3mbyte/sec through across openvpn.
and if i download 6 big files simultaneously, then the total throughput would hit the ceiling about 3.4mbyte/sec 

it would be nice if each time i download a file it would be 3.4mbyte/sec.
is there something wrong with my setting, mtu, or hardware.
i followed the guide here
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

