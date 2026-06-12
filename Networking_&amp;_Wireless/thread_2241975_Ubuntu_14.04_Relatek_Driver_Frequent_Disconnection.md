---
title: "Ubuntu 14.04 Relatek Driver Frequent Disconnection"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by rohit13 on 2014-08-29
I just installed ubuntu 14.04 on my new system which has realtek RTL8723BE wireless driver. The problem is it connects initially and then disconnects after a while. It will not work unless i reboot. 

I checked online and saw many faced the same issues. I wrote the following commands listed on a website, but it didnt have any effect.

sudo apt-get install linux-headers-generic build-essential git
git clone [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)
cd rtl8723be
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
make
sudo make install
sudo modprobe rtl8723be

Any one has a working solution ?

---

