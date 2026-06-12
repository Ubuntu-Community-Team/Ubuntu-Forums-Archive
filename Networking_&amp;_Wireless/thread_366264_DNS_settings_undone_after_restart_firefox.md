---
title: "DNS settings undone after restart firefox"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by qwasi_nodough on 2007-02-20
Hi there,

I've just installed Ubuntu 6.06 and i'm quite happy. Everything is straightforward upto now. Since the first time I started Ubuntu from the live-cd I had to manually configure the DNS in order to surf nicely. Now, after I installed permanently on /hdb, and I have installed all updates, every time I restart Firefox it won't return my homepage because the DNS isn't configerude right. It seems to me that I have to change the settings somewhere else than through the menu (system->administration->networking), could you help me in any way?

Cheers, Qwasi.

---

### Post by madmetal on 2007-02-20
you should edit resolv.conf 
open a terminal and write 
sudo gedit /etc/resolv.conf
then add your dns settings..

---

### Post by kerry_s on 2007-02-20
You add it to /etc/dhcp3/dhclient.conf using the prepend and it will be added to /etc/resolv.conf at every start. for example i use opendns service so i put->
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

sudo gedit /etc/dhcp3/dhclient.conf

---

### Post by qwasi_nodough on 2007-02-24
Thank you both! It was kerry_s' solution that eventually did the trick. It took me a while to remember that I had to be logged in as root, but than activating the 'prepend domain-name-servers' stuck. I also intuitively took out the domain-name-servers reference in the request. I'm not sure if it's wright, but every thing's still working. When I look at my network DNS settings now in the administration menu, it shows my 2 DNS adresses double. I gather they better be there twice than not at all.

Cheers again!

---

