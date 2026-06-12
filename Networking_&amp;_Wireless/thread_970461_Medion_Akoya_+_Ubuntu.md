---
title: "Medion Akoya + Ubuntu"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by martin_legion on 2008-11-04
Hello, I configured WIFI on a Medion Akoya on Ubuntu Hardy using ndiswrapper and the downloaded driver for windows. It worked for some time, but one day it stopped finding available signals.
What I did was:

sudo depmod -a
sudo modprobe ndiswrapper
echo ‘ndiswrapper’ | sudo tee -a /etc/modules
sudo ndiswrapper -m

echo ‘blacklist rt2860&#8242; | sudo tee -a /etc/modprobe.d/blacklist
echo ‘blacklist rt2860sta’ | sudo tee -a /etc/modprobe.d/blacklist 

and then in the directory containing the drivers:
sudo ndiswrapper -i rt2860.inf
sudo ndiswrapper -l 

As I said, it worked for a while, but now is dead... any ideas.
I don't recall updating or anything, but....

---

### Post by rosindda on 2009-02-11
Hi Martin,
          I have also a Medion laptop and can't connect via my wireless card. I am using a RT2860 chip set. How did you get yours connecting originally ? Which windows driver did you use ?

Thanks

---

### Post by martin_legion on 2009-02-12
> **rosindda said:**
> Hi Martin,
          I have also a Medion laptop and can't connect via my wireless card. I am using a RT2860 chip set. How did you get yours connecting originally ? Which windows driver did you use ?

Thanks

I've used this drivers:
[http://rapidshare.com/files/132471960/ralink_rt2860.tar.gz](http://rapidshare.com/files/132471960/ralink_rt2860.tar.gz)

And followed this tutorial (in spanish) but I'm sure it's a copy-paste from some other place because I've seen this tutorial replicated 100 times un 100 blogs:
[http://www.tuxapuntes.com/tux/content/view/973/126/](http://www.tuxapuntes.com/tux/content/view/973/126/)

---

