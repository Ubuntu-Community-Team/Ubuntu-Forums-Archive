---
title: "Cannot Detect Wireless Networks"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by timotsco on 2009-12-13
I have recently decided to start the plunge into open source operating systems, and have met little resistance from my computer, except with Wireless Networking.

I am running a dual boot system: Windows 7 Ultimate on one side, and Ubuntu 9.1 on this side. I live in an apartment building with about 15 wireless networks available for me to connect to, including my own (802.11g) network.

All of these networks are available within windows, and I can connect no problem. I also have a second laptop running windows 7 that is currently connected to my Wireless network, and can view the others. 

I am able to connect to the internet without hassle when i connect via Wired connection. I am new to this, but I have seen that i should post the following when i post a message for help like this:

```
timothy@Timothy-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:dd:4d:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.154 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff memory:f0000000-f00fffff(prefetchable)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```Any help that might be given, i thank you in advance, and it is appreciated.

Thanks

Tim

---

### Post by Temposs on 2009-12-13
Oh Broadcom, always causing trouble.

After a quick search, I found you should try this:

1) Install the b43-fwcutter package like this:
```
sudo apt-get install b43-fwcutter
```

2) Go to System->Administration->Hardware Drivers and disable and re-enable the driver for your Broadcom wireless card.

3) Restart your machine.

That should make your wireless card work. Let me know how it goes :-)

---

### Post by Greenwidth on 2009-12-13
> **Temposs said:**
> Oh Broadcom, always causing trouble.
You make Broadcom sound like a naughty child lol.

---

### Post by timotsco on 2009-12-14
[Thanks,]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8494905")

It works great now :)

---

### Post by scarrman on 2010-01-01
I had the same problem with Ubuntu 9.10 upgrade.  I also had to install (from Administration -> Hardware Drivers) 

Broadcom STA wireless driver

And then it worked for me as well.
Thanks a bunch!

---

