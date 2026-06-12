---
title: "how much room for kubuntu 9.10"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by mrcactu5 on 2009-11-28
How large should the partition be for installing Kubuntu 9.10?  I allocated 17GB and it won't let me find wireless networks, the documentation is missing and KReversi it spontaneously crashes.

Should I give Kubuntu room?

---

### Post by Temposs on 2009-11-28
17gb is more than enough. Your problems are not being caused by lack of space.

---

### Post by mrcactu5 on 2009-11-29
well... do you have any IDEAS?

Why can't I add wireless connections?

---

### Post by Greenwidth on 2009-11-29
Do you need to add a new connection to a working wireless adapter, or is it a new installation?

Have you a driver to activate in Hardware Drivers?

what is the model of your wireless adapter?
lspci (from terminal)

---

### Post by mrcactu5 on 2009-11-29
My computer comes with a wireless adapter.  It works on my Windows XP installation.  My Kubuntu was installed with Wubi.  

According to Hardware Drivers: "No proprietary drivers are in use on this system."

Here's the output for lspci:

[stuff]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

It probably has more information than I should be putting on the Internet but I think the last line says I have a Broadcom wireless controller.

---

### Post by Temposs on 2009-11-29
Yeah, Broadcom...Broadcom sucks for Linux compatibility. And it's probably even a worse situation with Wubi.

Anyway, instead of using Wubi, why don't you try installing Ubuntu with the Virtualbox program. It'll give you the same effect of running Ubuntu like a program within Windows, and it'll probably work better, because it won't rely on Ubuntu's drivers as much, so you'll probably get an internet connection if you try this.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Try this tutorial for how to install Ubuntu on Virtualbox. You'll probably have a good experience with this :-)

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by lykwydchykyn on 2009-11-29
> **mrcactu5 said:**
> My computer comes with a wireless adapter.  It works on my Windows XP installation.  My Kubuntu was installed with Wubi.  

According to Hardware Drivers: "No proprietary drivers are in use on this system."

Here's the output for lspci:

[stuff]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

It probably has more information than I should be putting on the Internet but I think the last line says I have a Broadcom wireless controller.

There's nothing dangerous about putting that information on the internet.  Both of those broadcom cards can work fine with Linux, you just need to install the drivers.  Does the hardware drivers tool offer any proprietary drivers to activate?  Can you connect to a network using a cable?

EDIT: my laptop has the same wireless driver.  I had to activate a driver called "Broadcom STA" in the hardware drivers tool.

---

### Post by mrcactu5 on 2009-12-09
I am connected to the Internet now by Ethernet cable.  Hardware Drivers now says "Broadcom B43 Wireless Driver" and "This driver is activated and currently in use."  Nonetheless, when I go to "network connections" I can't add a wireless (eth1) connection.   When I click KNetworkManager nothing happens.

---

### Post by lykwydchykyn on 2009-12-09
What's the output from 
```

/sbin/ifconfig -a

```

---

### Post by mrcactu5 on 2009-12-09
/sbin/ifcongif -a spits out the following:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:ef:ed:e1
          inet addr:169.231.16.141  Bcast:169.231.17.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:68ff:feef:ede1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7814 errors:0 dropped:57 overruns:0 frame:0
          TX packets:1771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1902144 (1.9 MB)  TX bytes:353354 (353.3 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12564 (12.5 KB)  TX bytes:12564 (12.5 KB)
```

I think the first is my ethernet cable, and the second is localhost.

---

### Post by lykwydchykyn on 2009-12-09
Try this:
```

sudo modprobe b43

```

Then see if eth1 shows up.  If not, post the output of:
```

dmesg |tail

```

---

### Post by mrcactu5 on 2010-01-03
sudo modprobe 43 returns nothing.

dmesg |tail returns the following:

```
[   31.737324]  domain 0: span 0-1 level SIBLING
[   31.737337]   groups: 0 1
[   31.737359] CPU1 attaching sched-domain:
[   31.737369]  domain 0: span 0-1 level SIBLING
[   31.737391]   groups: 1 0
[   46.246724] sreadahead[410]: segfault at 0 ip 080499cd sp bf98ddf0 error 4 in sreadahead[8048000+3000]
[  376.924430] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  376.924445] tg3: eth0: Flow control is off for TX and off for RX.
[  376.925247] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  387.804123] eth0: no IPv6 routers present
```

---

### Post by lykwydchykyn on 2010-01-04
> **mrcactu5 said:**
> sudo modprobe 43 returns nothing.

That means it did its job with no errors.
> 
dmesg |tail returns the following:

```
[   31.737324]  domain 0: span 0-1 level SIBLING
[   31.737337]   groups: 0 1
[   31.737359] CPU1 attaching sched-domain:
[   31.737369]  domain 0: span 0-1 level SIBLING
[   31.737391]   groups: 1 0
[   46.246724] sreadahead[410]: segfault at 0 ip 080499cd sp bf98ddf0 error 4 in sreadahead[8048000+3000]
[  376.924430] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  376.924445] tg3: eth0: Flow control is off for TX and off for RX.
[  376.925247] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  387.804123] eth0: no IPv6 routers present
```

That's a bit odd.  the b43 driver is the correct driver for that hardware.  Assuming the hardware is on, there should be some indication that it's detected and activated after loading the driver.  But there isn't.

Are you dual booting here?  Does it work in another OS?  What about from the liveCD/USB?  Any switches in BIOS or on the case to toggle the wireless?

---

### Post by mrcactu5 on 2010-01-12
I am using Wubi.  My wireless works fine in Windows.

---

### Post by conorsulli on 2010-01-12
One time I also had a strange issue like this...

This is a very "out of the box" reply as I cant really remember what caused it... assuming synaptic still comes with kubuntu open it up....

type in "Broadcom"... you should have the two bcmwl-modailases and bcmwl-kernel-source installed. Install b43-cutter and now re-open "hardware drivers" and check if a new option crops up and install that one instead... by the way you should reboot inbetween installing the broadcom driver.

Basically I used to use this one before the other one didn't work.. however it fixed with the latest updates.

So I reccomend rather that first make sure if it is a new install update everything first. (unistall any hardware driver first from the "hard-ware drivers") and retry... use the default one first and only then if it doesn't work try my other method with the b43-cutter driver.

Again its strange but I had the same issue it seems.

EDIT: Just checked, I also have the same broadcom version as you!

---

### Post by mrcactu5 on 2010-01-16
I installed the proprietary wireless driver and turned the computer on and off a couple times.  Magically I get wireless.  Problem solved, but not good explanation why.

---

### Post by conorsulli on 2010-01-16
Yeah, I had the same wierd issue....

---

