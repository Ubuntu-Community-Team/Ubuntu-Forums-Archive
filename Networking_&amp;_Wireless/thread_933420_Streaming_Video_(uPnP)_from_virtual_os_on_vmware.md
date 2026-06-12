---
title: "Streaming Video (uPnP) from virtual os on vmware?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by xMemphisx on 2008-09-29
I'm trying to setup a virtual windows xp professional using vmware in ubuntu 8.04 x64 that will stream videos (like windows normally would), with TVersity. I have the virtual version of XP up and running, and i have tversity on, but my PS3 doesn't see any media servers. I tried changing the connection on the virtual machine from NAT to 'bridged', but when i make the change i get 'limited or no connectivity'. I do have MAC address filtering ON, for my Belkin wireless router... but i added the address from the virtual machine to the list and i'm still getting limited or no connectivity. when I hit 'repair', it just sits at "aquiring network address" for maybe a full minute and then says limited or no connectivity.

The only other information i can think of that might be pertinent is the ubuntu box itself connects to the network via WiFi... but vmware itself IS configured for wlan0 as the device to use, NOT eth0 (NAT works just fine)

---

### Post by nixscripter on 2008-09-29
Virtual boxes are nearly always a mess.

The only thing that seems to work for me is 1 to 1 NAT. I don't know how to do it for vmware, but the general idea is this.

Suppose your Ubuntu machine is connected to the "real" network with the IP 192.168.0.2

1. Set up a [TAP device]("http://vtun.sourceforge.net/tun/faq.html#1.2") on Ubuntu with an imaginary address, like 10.0.0.1.
2. Have VMware use the tap device as the "real hardware" network card. Have it assign itself a static IP of 10.0.0.2 and gateway of 10.0.0.1
3. Create a second IP for the real Ubuntu interface (wlan0), say 192.168.0.3
4. Using IP tables, map 10.0.0.2 on the tap device to 192.168.0.3 on the real device and back.

I've found this will forward everything properly, including UDP, which most NAT configurations will filter out. I don't know about broadcasting, however.

Hope this helps.

---

### Post by xMemphisx on 2008-09-29
Is there a way to get tap working for 64-bit ubuntu?

---

### Post by nixscripter on 2008-09-29
I don't know about 64-bits, but at least 32-bit Ubuntu comes with it built in.

First load the kernel module: ```
sudo modprobe tun
``` And then use the **tunctl** utility to set up the interface (see the man page for more details).

If it's not built in (which would surprise me), I suppose you could compile it yourself. Download it here: [http://vtun.sourceforge.net/tun/tun-1.1.tar.gz](http://vtun.sourceforge.net/tun/tun-1.1.tar.gz)

By the way, in case I didn't make myself clear, there are two parts to a TAP device: the interface (tap0) and the device (/dev/tap0). VMware will open /dev/tap0 and use it for networking, which probably means it will need to be run with special options. That's what I don't know how to do.

---

