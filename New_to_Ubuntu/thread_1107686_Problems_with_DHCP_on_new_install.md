---
title: "Problems with DHCP on new install"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-27
Hi I just finished installing Xubuntu on an older Computer of ours and during the alternate CD installation I skipped the DHCP configuration because the automatic configuration wasn't working. I didn't have an ethernet jack close by and was intending to use a wireless USB stick that I would plug in later on.

Now I have it installed and running, and it recognizes my USB stick fine and even connects to our wireless network - but the internet won't work and it won't download updates. I figured it's because I didn't set up DHCP during installation.. but I have no idea how to fix it now.

I have tried adding the following to /etc/network/interfaces but it didn't make a difference.

auto wlan0
iface wlan0 inet dhcp


And then I ran ifup wlan0 which told me that it had already been configured...

There is a couple of lines that are at the start of the interfaces file that specify something about looping back or something a rather that I have never seen before... do I need these? Is this relevant?

Please help!

---

### Post by humphreybc on 2009-03-27
Anybody?

---

### Post by BDNiner on 2009-03-27
What happens if you assign the computer a static ip address? The interfaces file is not used much. You can set a static ip address from the network control applet on the taskbar.

---

### Post by humphreybc on 2009-03-27
What IP address should I use? Sorry i'm not very good at networking at all!

---

### Post by Iowan on 2009-03-27
Just for a trial, make a backup copy of our /etc/network/interfaces, then replace wan0 with eth0.  I suspect it won't work. The new Network Manager saves it's configuration files in */etc/NetworkManager/nm-system-settings.conf*. You can verify that eth0 exists with **lshw -C network**.

---

