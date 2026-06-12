---
title: "PROXY problems (connection via router)"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by -=MindHunteR=- on 2008-04-09
Hello! I have a computer, let's call it BLACKBOX, which connected to big external LAN network, and has DHCP IP address. The second network card has constant IP 192.168.0.1 on this computer connected to wireless router, and thru it my notebook connected. Ubuntu is running on BLACKBOX. Everything works fine!  When I connect to proxy server on BLACKBOX, making ssh -D 12345 blah blah blah, I can surf on BLACKBOX when I configure Mozilla to connect thru localhost:12345 SOCKS5. However, when I trying configure Mozilla on notebook to connect thru 192.168.0.1:12345 SOCKS5 I can't surf and receive this message, that proxy isn't configured properly. In the same time all others services which use internet working properly on notebook.

What can be the problem?

Thanks.

---

