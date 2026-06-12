---
title: "No network after memory upgrade"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by vvgb on 2011-05-25
Hello,

I've got a Desktop Acer Aspire M1100 running Ubuntu 10.04 LTS - Lucid Lynx  for 64 bits. So far, it has been running with no problems, with 1 GB RAM.

Now I want to upgrade the RAM to 4 GB. I've purchased two modules of 2Gb (ACER-2GB-DDR2-800-D) 

When I put only one of the modules, everything works ok.

But when I insert both modules, the network adapter doesn't work!!. Although the ethernet link seems to be up (the led is green), the adapter neither gets an address from DHCP nor sends packets when using manually fixed ip address. The rest of the system apparently works ok, and the system shows 3.6GiB RAM.

The adapter is a Marvel Yukon 88E8056 PCI Gigabit Ethernet, integrated in the mother board.

It seems to be a problem related to Ubuntu handling of the RAM and the memory space reserved to the network adapter, but I'm not able to fix it.

Any ideas?

---

### Post by terrykiwi83 on 2011-05-25
I can honestly say I would never of guessed it was possible for the RAM to have an affect on your network adapter.

Just as a suggestion try the live CD for 11.04 natty or for your current version and see if its the same?

---

### Post by wildmanne39 on 2011-05-26
> **vvgb said:**
> Hello,

I've got a Desktop Acer Aspire M1100 running Ubuntu 10.04 LTS - Lucid Lynx  for 64 bits. So far, it has been running with no problems, with 1 GB RAM.

Now I want to upgrade the RAM to 4 GB. I've purchased two modules of 2Gb (ACER-2GB-DDR2-800-D) 

When I put only one of the modules, everything works ok.

But when I insert both modules, the network adapter doesn't work!!. Although the ethernet link seems to be up (the led is green), the adapter neither gets an address from DHCP nor sends packets when using manually fixed ip address. The rest of the system apparently works ok, and the system shows 3.6GiB RAM.

The adapter is a Marvel Yukon 88E8056 PCI Gigabit Ethernet, integrated in the mother board.

It seems to be a problem related to Ubuntu handling of the RAM and the memory space reserved to the network adapter, but I'm not able to fix it.

Any ideas?Hi double check that your ethernet card is in good when you get both of your rams installed, also are the both the same ram, made for that desktop, I agree I have never heard of that problem before, thats why I think you probably have a bad connection with your card and the motherboard.

---

### Post by vvgb on 2011-05-27
Thank you for your answers, I'm sure it's not a problem with the connections because I've tried several times and it works with one module and it doesn't work with two.
Besides, booting from another partition with Windows Vista it works with the two modules (although windows is able to see only 3070 MB)

Terrykiwi83, it seemed a goog idea using a live CD, so I tried. 
But then I discovered that (when the two modules are inserted) the CD unit doesn't work either.

I think I'll try to update to 11.04...

---

### Post by josephmills on 2011-05-27
hi there could we please see a ```
sudo lshw -C network
``` thanks

---

### Post by vvgb on 2011-05-27
Hi,
this is the output to **sudo lshw -C network** when only 1 module of 2GB is used:

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:3f:13:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A **ip=192.168.1.130** latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:fddfc000-fddfffff ioport:ee00(size=256) memory:fdc00000-fdc1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

When both modules of 2GB are used the output is almost the same, but the words **ip=192.168.1.139** are not shown now:

-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:3f:13:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:fddfc000-fddfffff ioport:ee00(size=256) memory:fdc00000-fdc1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Thanks

---

### Post by wildmanne39 on 2011-05-28
> **vvgb said:**
> Hi,
this is the output to **sudo lshw -C network** when only 1 module of 2GB is used:

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:3f:13:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A **ip=192.168.1.130** latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:fddfc000-fddfffff ioport:ee00(size=256) memory:fdc00000-fdc1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

When both modules of 2GB are used the output is almost the same, but the words **ip=192.168.1.139** are not shown now:

-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:3f:13:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:fddfc000-fddfffff ioport:ee00(size=256) memory:fdc00000-fdc1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Thanks
Hi, I noticed towards the bottom of the read out it said network disabled, I think you should look there. Also I noticed it mentioned virtualbox, is this in a vm?

---

### Post by crispy_420 on 2011-05-28
I know it is not a VM issue but when ever I bump a 32-bit VM to 4GB it kills the NIC on said VM. Drop it down and it works again. Saw it happen in Windows Server 2003 too.

---

### Post by wildmanne39 on 2011-05-28
> **crispy_420 said:**
> I know it is not a VM issue but when ever I bump a 32-bit VM to 4GB it kills the NIC on said VM. Drop it down and it works again. Saw it happen in Windows Server 2003 too.
Hi, for 4 gigs to work properly you need 64 bit or pae installed, but still do not know why that would mess up networking.

---

### Post by wildmanne39 on 2011-05-28
> **crispy_420 said:**
> I know it is not a VM issue but when ever I bump a 32-bit VM to 4GB it kills the NIC on said VM. Drop it down and it works again. Saw it happen in Windows Server 2003 too.
Hi,you might also try changing the network adapter settings in virtual box, it cant hurt and you can always change them back.

---

### Post by Old_Grey_Wolf on 2011-05-28
Have you tried the the VirtualBox "Intel PRO / 1000 MT (82540EM)" setting for the network adapter?

---

### Post by VanR on 2011-05-28
May be obvious, but did you run memtest to make sure BOTH of your new memory sticks are good?

---

### Post by crispy_420 on 2011-05-29
> **wildmanne39 said:**
> Hi,you might also try changing the network adapter settings in virtual box, it cant hurt and you can always change them back.

As soon as I dropped back down to 3200MB it worked again. Tried messing with network adapters and reinstalling vbox drivers too. The NIC actually vanished in guest OS until RAM dropped. Leads me to believe it was OS + 4GB limitation.

Here is reference in another forum on the issue:
[http://forums.opensuse.org/network-internet/412787-no-network-after-update-ram-4gb.html](http://forums.opensuse.org/network-internet/412787-no-network-after-update-ram-4gb.html)

They seem to think either a memory addressing issue or even a BIOS limitation/setting.

But the original author has an issue with physical hardware so really no need to further vbox talk. So maybe a BIOS update may be in order. Often these updates address one of two things: new CPU support or to extend memory compatibility. Is a BIOS current or original factory?

---

### Post by vvgb on 2011-05-29
Hi again,

I tried to disable the virtualbox network, then I deleted the virtual machine and finally I uninstalled the virtualbox software. None of those actions solved the problem. The vbox interface is not there for more so it cannot hurt, but the problem is still unsolved.

Then I updated to 11.04 Natty. The new thing is that the cd unit is working now (!!??). The network adapter is not working yet when 4Gb ram are used-
As the CD unit is working, I booted from a live cd just to try and see the difference, but the behaviour is identical.

These are the relevant system messages when booting with only 2GB RAM:

May 28 23:11:43 vt3 kernel: [    1.576172] sky2: driver version 1.28
May 28 23:11:43 vt3 kernel: [    1.578895] sky2 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 28 23:11:43 vt3 kernel: [    1.578911] sky2 0000:02:00.0: setting latency timer to 64
May 28 23:11:43 vt3 kernel: [    1.578955] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
May 28 23:11:43 vt3 kernel: [    1.579046] sky2 0000:02:00.0: irq 41 for MSI/MSI-X
May 28 23:11:43 vt3 kernel: [    1.579698] sky2 0000:02:00.0: eth0: addr 00:1c:25:3f:13:5b
May 28 23:11:48 vt3 kernel: [   17.427327] sky2 0000:02:00.0: eth0: enabling interface
May 28 23:11:48 vt3 kernel: [   17.427807] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 23:11:49 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 28 23:11:50 vt3 kernel: [   19.134723] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
May 28 23:11:50 vt3 kernel: [   19.135080] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 28 23:11:52 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 28 23:11:52 vt3 dhclient: DHCPOFFER of 192.168.1.130 from 192.168.1.1
May 28 23:11:52 vt3 dhclient: DHCPREQUEST of 192.168.1.130 on eth0 to 255.255.255.255 port 67
May 28 23:11:52 vt3 dhclient: DHCPACK of 192.168.1.130 from 192.168.1.1
May 28 23:11:53 vt3 dhclient: bound to 192.168.1.130 -- renewal in 103519 seconds.
May 28 23:11:58 vt3 NetworkManager[838]: <info> (eth0): carrier is ON
May 28 23:11:58 vt3 NetworkManager[838]: <info> (eth0): new Ethernet device (driver: 'sky2' ifindex: 2)
May 28 23:11:58 vt3 NetworkManager[838]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 28 23:12:00 vt3 kernel: [   29.890023] eth0: no IPv6 routers present


And these are when booting with 4GB RAM - ERRORS-:

May 28 23:35:28 vt3 kernel: [    1.674679] sky2: driver version 1.28
May 28 23:35:28 vt3 kernel: [    1.675241] sky2 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 28 23:35:28 vt3 kernel: [    1.675255] sky2 0000:02:00.0: setting latency timer to 64
May 28 23:35:28 vt3 kernel: [    1.675294] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
May 28 23:35:28 vt3 kernel: [    1.675384] sky2 0000:02:00.0: irq 41 for MSI/MSI-X
May 28 23:35:28 vt3 kernel: [    1.676074] sky2 0000:02:00.0: eth0: addr 00:1c:25:3f:13:5b
May 28 23:35:28 vt3 kernel: [   26.070066] sky2 0000:02:00.0: eth0: enabling interface
May 28 23:35:28 vt3 kernel: [   26.070076] sky2 0000:02:00.0: error interrupt status=0x80000000
May 28 23:35:28 vt3 kernel: [   26.070084] sky2 0000:02:00.0: PCI hardware error (0x2010)
May 28 23:35:28 vt3 kernel: [   26.081038] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 23:35:28 vt3 NetworkManager[648]: <info> NetworkManager (version 0.8.3.998) is starting...
May 28 23:35:28 vt3 NetworkManager[648]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 28 23:35:28 vt3 NetworkManager[648]: <info> (eth0): carrier is OFF
May 28 23:35:28 vt3 NetworkManager[648]: <info> (eth0): new Ethernet device (driver: 'sky2' ifindex: 2)
May 28 23:35:28 vt3 NetworkManager[648]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 28 23:35:29 vt3 NetworkManager[648]: <info> (eth0): carrier now ON (device state 1)
May 28 23:35:29 vt3 kernel: [   27.753473] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
May 28 23:35:29 vt3 kernel: [   27.755983] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
**May 28 23:35:29 vt3 kernel: [   27.770071] sky2 0000:02:00.0: error interrupt status=0x80000000**
**May 28 23:35:29 vt3 kernel: [   27.770079] sky2 0000:02:00.0: PCI hardware error (0x2010)**
May 28 23:35:31 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 28 23:35:34 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 28 23:35:41 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 28 23:35:41 vt3 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
[B]May 28 23:36:29 vt3 dhclient: No DHCPOFFERS received
[/B]
I've got an easy workaround: I've installed an old FastEthernet NIC I kept from an old computer, and it works. The "only" difference is that it's an independent PCI card, whilst the Marvel Yukon is integrated in the mother board.

Anyway, it's kind a challenge to solve the problem.

Old_Grey_Wolf, crispy_420: I'm not going on investigating more about virtualbox drivers at the moment, as I could uninstall them without losing any important application. But it seems interesting your suggestions about updating BIOS. Also, I'd like to have a better understanding on the PCI memory buffers allocation.

Thanks

---

### Post by crispy_420 on 2011-05-29
It sounds like it was a BIOS/memory issue. That is what is was trying to say. It has nothing to do with vbox at all, I was using it as an example of the effects of memory. It is an architectural issue with the OS and large RAM amounts just like the suse forum link. 

As long as it works right?

---

### Post by vvgb on 2011-05-30
Yes crispy_420, you're right it's an architectural problem, it matches the links you posted.
Then my workaround is going to be the definitive solution.

Thanks

---

### Post by crispy_420 on 2011-05-30
Nothing beats a free fix right? Sometimes keeping old hardware component pays off.

Maybe a BIOS update might be a fix but it comes with risk. If it works now why risk it.

---

