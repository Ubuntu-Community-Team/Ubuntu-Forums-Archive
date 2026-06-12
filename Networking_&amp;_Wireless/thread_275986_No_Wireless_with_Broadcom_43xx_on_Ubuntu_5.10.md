---
title: "No Wireless with Broadcom 43xx on Ubuntu 5.10"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by codecraig on 2006-10-12
So i have Ubuntu 5.10 installed on a Dell Latitude D820 laptop which has a Broadcom 43xx wireless card.  I tried using several suggestions mentioned on these forums...such as...

sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper


....however, my Ubuntu didn't have ndiswrapper, and I don't have a wire connection so I can't download it.  Anyone get this working?

I am dual booting with Win XP.  If this won't work I am gonna have to use Red Hat or Suse, since it appears Dell at least has a driver for those.

Thanks in advance.

---

### Post by weijie90 on 2006-10-12
why not just use an ethernet connection at a friend's place?

---

