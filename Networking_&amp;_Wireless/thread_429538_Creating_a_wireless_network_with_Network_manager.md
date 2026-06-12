---
title: "Creating a wireless network with Network manager"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by joelcogen on 2007-05-01
Hi,

I'm using Feisty, and wireless works perfectly with madwifi and Network manager.

But when I try to create my own wireless network, it tries and then connects to my favorite network, without even saying it failed. I'm trying to host a network so that people can connect to me and play... I tried to connect to a windows ad-hoc wireless, but I can't, so the only options seems to create it under linux, and have everybody connect to it.

Anyway, did anyone successfully hosted a wireless network? Should I configure something, or install some other drivers ?

BTW, I had to modify /etc/network/interfaces to install Network manager. It looks like this:
--
  auto lo
  iface lo inet loopback
--

Thank !

Joel

---

### Post by flukierdonut on 2007-05-08
well im no expert here but from what i've read from other forums it seems as if though no channel is set when creating a ad-hoc network. maybe try this:
sudo iwconfig wlan0 mode ad-hoc essid networkname channel 6
then just replace the channel and ESSID to whatever you want. a link to the the original post is below:
[http://justlinux.com/forum/archive/index.php/t-147208.html]("http://justlinux.com/forum/archive/index.php/t-147208.html")

---

### Post by joelcogen on 2007-05-08
I tried that iwconfig thing, but here's what it says:

$ sudo iwconfig ath0 mode ad-hoc essid Test channel 11
Error for wireless request "Set Mode" (8B06) :
  SET failed on device ath0 ; Invalid argument.

I checked the spelling, and everything is ok, apparently the driver doesn't support mode set to ad-hoc... :(

Anything I can do ? Using ndiswrapper maybe ?

Thanks for your reply anyway :D

---

### Post by asr4work on 2007-05-13
In fact, the syntax of iwconfig is good.
But the problem is
- there is a daemon regularly changing the manual settings (in my case, the bomobolong essid WITHOUT WEP nor WPA to build a "reseau citoyen)
- the wifi network manager doesn't support any unscrambled network

By the way, there is another daemon regularly remounting any partition unmounted.

This distribution seems to be more and more complex as the time it grows, and starts to become hard to maintain "the old way", ie. via commands & scripts.
In other owrds : what is really the advantage of using a linux distribution working the same as a windows : via the GUI ?

---

