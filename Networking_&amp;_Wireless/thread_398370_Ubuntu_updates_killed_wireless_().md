---
title: "Ubuntu updates killed wireless (??)"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by ab-hammer on 2007-03-31
I downloaded and installed the latest ubuntu last week.  Everything worked great, including the wireless nic.  I set up email, started firefox, etc, and was thoroughly enjoying the experience.

Today the updater came up saying I had some 260 or more updates to apply.  A big list - too much to look at in detail (or so I thought), so I told it to go ahead.  After the updates were done, I restarted (as required) and everything was fine except the wireless disappeared.  Here's what I have found so far ...

The machine is an old Pentium 2.  The only nic is a belkin with the prism chipset.  It worked minutes before, and now it doesn't.  Strange. 

So I dig a little and discover I can do this ...

mine:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
       resources: iomemory:e6001000-e6001fff irq:5

Hmmm ... as far as I can tell, everything looks ok, but why is *-network DISABLED?
Dig some more and discover lsmod. A lot of stuff here, but these are the only network related entries:

mine:~$ sudo lsmod
Module                  Size  Used by
ipv6                  272288  8 
prism2_pci             74752  0 

No wlan or eth ... I think there should be one there.  Ok, dig around some more and discover the /etc/network/interfaces file
I have never looked at this file before, so have no idea if this looks right:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-essid MYNETWORK
wireless-key ****all the hex key is here***

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Then I remember seeing something that said I should also look at /etc/iftab

wlan0 mac 00:00:00:00:00:00 arp 1

Uh oh ... that MAC doesn't look right.  Dig some more and discover the sudo ifconfig command.  The only thing it shows is the "lo" device, which apparently is the loopback.  No eth0 or wlan0 or whatever should appear there.

I am sure you often hear "but I didn't do anything" only to discover later that they did.  For what it's worth, I say with hand on heart that "I didn't do anything" other than let ubuntu install its updates.  The machine was not moved or bumped or kicked, no one clicked anything else, etc.  The network worked before the updates.  Now it doesn't.  I find it a little hard to accept that this would be a hardware problem.

This hits the limit of my linux knowledge.  Why doesn't ubuntu see the nic anymore?  Does ubuntu give me a magic app that will rediscover my hardware?

---

### Post by Floppyjoe on 2007-03-31
Make sure you have linux-wlan-ng and linux-wlan-ng-firmware installed

---

### Post by ab-hammer on 2007-04-01
Thank you!  =D> 

Since the machine was dead to the net, I had to download the files elsewhere and use a memory stick to get them where they were useful.  I like the simple installation of the DEB files ... double click and say "install" (hopefully this won't mess up the automated updates in the future).  Then I used the Networking app to enable the device and set up the encryption again, and all was well.

In case anyone else runs into this issue, the files can be found at [http://packages.ubuntulinux.org/edgy/admin/linux-wlan-ng](http://packages.ubuntulinux.org/edgy/admin/linux-wlan-ng) and [http://packages.ubuntulinux.org/edgy/admin/linux-wlan-ng-firmware](http://packages.ubuntulinux.org/edgy/admin/linux-wlan-ng-firmware)

---

### Post by tfmorris on 2007-04-25
This problem also affects the Linksys WMP11 which is based on the Prism 2.5 chip.  I was using the recommended incremental update to get from Dapper to Edgy to Feisty on a machine which only had wireless Ethernet, no hardwired NIC, so of course I was completely screwed when the upgrade failed in this way.

The linux-wlan-ng-firmware wasn't necessary to get back on the air in my case.  It had an additional 18 dependencies, so I figured I'd try without it rather than shuttle the rest of the packages back and forth via sneaker net.  I was able to get things running well enough to download that package and its dependencies over the wireless connection.  Your mileage may vary, but it's worth a try if you end up in the same situation.

I don't know how popular Prism based cards are, but this seems like a pretty fundamental miss in the upgrade process.  I was updating from a current network repository too, so it's apparently not a problem which has been patched although the release has been out for a while.

Tom

---

### Post by engin on 2007-05-09
Thanks a lot guys, this thread was a life saver. My wireless (which is also recognized as prism2.5) stopped working since I upgraded to feisty. Installing linux-wlan-ng and restarting network service worked like a charm.

---

