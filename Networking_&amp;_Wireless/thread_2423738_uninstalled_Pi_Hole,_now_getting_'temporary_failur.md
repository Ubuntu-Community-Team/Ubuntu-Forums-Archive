---
title: "uninstalled Pi Hole, now getting 'temporary failure in name resolution"
date: 2019-07-28
forum: Networking &amp; Wireless
---

### Post by thejim on 2019-07-28
I installed DoH and Pi Hole on my laptop using this guide:  [https://docs.pi-hole.net/guides/dns-over-https/](https://docs.pi-hole.net/guides/dns-over-https/)
then I decided to buy a Raspberry Pi 4 and install Pi Hole on that.  
I then tried to remove cloudflared and Pi Hole from my laptop but now the networking isn't working.
The gui tools show I'm getting IP address and DNS servers correctly from my router, but when I ping I get error "Temporary failure in name resolution", VNC Server isn't connecting, can't run apt update, my browser can't load webpages, etc.

I found that /etc/resolv.conf had this line "nameserver 127.0.0.1" and I changed it to "nameserver 1.1.1.1" and that got things working.  But my understanding is that this is temporary until the next reboot when that file gets automatically overwritten.

any ideas how to get the network working again, permanently?

I searched google and found many other people having same issue and there were several possible solutions but none of them worked for me so I decided to do a clean re-install

---

