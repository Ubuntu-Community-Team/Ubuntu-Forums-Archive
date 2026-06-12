---
title: "ubuntu 10.04 wireless, theme, and open program"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by Andi_Abdul_Syukur on 2015-11-30
[TABLE]
[TR]
[TD="class: votecell"]         0         down vote          [favorite]("http://askubuntu.com/questions/703049/ubuntu-10-04-cant-detect-any-wireless-network-and-only-use-wired-network?noredirect=1#")[/TD]
[TD="class: postcell"]        1. hi i'm using ASUS A46C and my Network controller: Atheros  Communications Inc. Device 0032 (rev 01). now i'm still using 10.04  along with 15.10. in 15.10 i can use wireless automaticly but in 10.04  it seems there's no network found. i'm using some reaserch type lshw -c  network and the result is 

<p>WARNING: you should run this program as super-user.   *-network UNCLAIMED
       description: Network controller        product: Atheros Communications Inc.        vendor: Atheros Communications Inc.        physical id: 0        bus info: pci@0000:03:00.0        version: 01        width: 64 bits        clock: 33MHz        capabilities: bus_master cap_list        configuration: latency=0        resources: memory:f7900000-f797ffff memory:f7980000-f798ffff(prefetchable)   *-network        description: Ethernet interface        product: RTL8111/8168B PCI Express Gigabit Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0.2        bus info: pci@0000:04:00.2        logical name: eth0        version: 0a        serial: 08:60:6e:99:bc:f8        width: 64 bits        clock: 33MHz        capabilities: bus_master cap_list ethernet physical        configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.4 latency=0 multicast=yes        resources: irq:28 ioport:d000(size=256) memory:f2104000-f2104fff(prefetchable) memory:f2100000-f2103fff(prefetchable)</p>

<p>2. i have installed many themes but when i open synaptic the window's style is same with other themes but 3 days before, the theme synaptc windows's was following the theme i chose maybe some package's broken but seem there's no problem when i open synaptc

<p>3. when i open keyrix.py it execute with gedit despite as a programs i don't know what's wrong with my ubuntu 

  please explain me more details because i still noob in linux dist and please don't say upgrade the OS because i loved it. thanks[/TD]
[/TR]
[/TABLE]

---

### Post by coffeecat on 2015-11-30
I see you simply copy-pasted from your askubuntu question here: [http://askubuntu.com/questions/703049/ubuntu-10-04-cant-detect-any-wireless-network-and-only-use-wired-network](http://askubuntu.com/questions/703049/ubuntu-10-04-cant-detect-any-wireless-network-and-only-use-wired-network)

The answer is going to be the same here as on askubuntu: the problem you have is in an unsupported and obsolete version of Ubuntu, which we can't help you with.  If I read your post correctly, you are not having the wireless problem in Ubuntu 15.04 or 15.10. The fix is simple: don't use 10.04, use a later and supported release.

By the way, we don't object to you posting the same thing here and on askubuntu, but please do not simply copy-paste from the askubuntu page. That is why you managed to include a lot of spurious formatting and other stuff. It looks sloppy and is likely to put people off from helping you. Please copy-paste, if you must, from your original draft

---

### Post by Andi_Abdul_Syukur on 2015-11-30
the reason i don't use 11.10 and above because it's very hot. i got 80C when i'm using libre office and only it. i install thermald, tlp doesn't work i change again laptop mode no working too, and my laptop still hot until it gets hang. i have update the OS and then install NVIDIA still hot but when i'm using 10.04 and i play psx1 no hotin my laptop

---

### Post by coffeecat on 2015-11-30
Then I suggest you start a new thread to get help about over-heating in your laptop. Perhaps you need a lighter variant of Ubuntu such as Xubuntu or Lubuntu, or maybe there is another solution. We cannot help you with a release of Ubuntu which is well past its end-of-life.

---

