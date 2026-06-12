---
title: "Dell XPS 13 wireless connection limited to 1 MBit/s"
date: 2017-05-13
forum: Networking &amp; Wireless
---

### Post by sehfahrer on 2017-05-13
Hi there and thanks in advance for your assistance!

I just recevied my brand new XPS 13 with ubunut 16.04 lts installed. Everything works out of the box but my wireless connection is limited to 1 MBit/s, which is pretty annoying.

Doing some research, I found one thread from a guy with a similar problem [https://ubuntuforums.org/showthread.php?t=2354499](https://ubuntuforums.org/showthread.php?t=2354499) only it doesn't seem to be resolved.

I did run that same script and its output is attached to this post (I hope).

I suspect it is some kind of configuration problem on the driver side but I have no idea on how to deal with that.

Can anybody help, please?

Thanks!

---

### Post by Hadaka on 2017-05-14
Hi, from a working wired connection please copy and paste
one line at a time..
```
sudo apt-get update
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
router wifi configuration is currently set for wpa1 / wpa2
TKIP...if possible please change that to wpa2 aes NO tkip
please also set network manager settings for Ipv6 to Ignore
post the output of ..
```
cat /etc/network/interfaces
```
Thanks

---

