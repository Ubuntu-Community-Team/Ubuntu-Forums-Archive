---
title: "Network is working but Internet is unstable"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by pallko on 2008-10-17
I have installed UBUNTU 8.04.1 on a via CN10000EG board, and the network works fine when I browse and copy/move files across the local network, but when I try to browse the internet, the connection seems to stop or block after a very short time, so the browser never gets the whole html page, just a part of it. 

It doesn't matter what site I am browsing, I never get the whole html page, and if I refresh the page it doesn't stop the same place every time.

I have tried to boot on a live DSL, and then every thing works fine, so the problem isn't hardware related. And although I am sitting behind a firewall, it doesn't block the internet when I am using DSL, so I don't see why it should block UBUNTU.

Does anybody have a suggestion on how to pursue this problem?

-Palle

---

### Post by pallko on 2008-10-17
Actually there are some sites that I can browse without problems, but only a few. One is [http://www.mozilla-europe.org](http://www.mozilla-europe.org) but the problem is not related to firefox alone, as apt-get update doesn't work either! the repositories can't be downloaded, and the same goes for Update manager!

-Palle

---

### Post by superprash2003 on 2008-10-17
try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220
for reference : [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by pallko on 2008-10-20
I have just tried to change the DNS addresses, but it didn't make any change at all.

:(

-Palle

---

