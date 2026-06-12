---
title: "CLI install wireless-tools quesiton"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by alterKrieg on 2010-02-12
After installing ubuntu command line only, I'm struggling to get the wireless to work.  It works perfectly on the regular install, but the CLI does nothing for me.

I followed some other advice, and installed wireless-tools, libc6 (udev), libiw29 packages from packages.ubuntu.com.

The cmd line noob question I have now is: how do I use these tools to get my wireless connected?

---

### Post by gordintoronto on 2010-02-12
What follows comes from another thread, I am not the author:

"It will work perfectly with a static IP address in /etc/network/interfaces. My interfaces file, with a few details disguised, is here:
Quote:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096xxxxAFE

#auto eth0
iface eth0 inet dhcp

"Before login, the network is up and running. I have tested and run this on home servers many times."

In other words, all you have to do is make your interfaces file correct.

I won't ask why you're torturing yourself by running command-line only...

---

