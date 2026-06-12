---
title: "Ubuntu Server 14.04 LTS: (LAN) Network dropping every 12 hours or so"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by buntu_hugenewbie11 on 2014-09-12
I have recently installed Ubuntu Server on Dell PowerEdge T310 Server with the PERC 6/i SAS internal RAID adapter (PCI Express).
I have the server connected to the institution's network which is supposed to give me a static IP based on the MAC.
Every night I find that the server goes down and I have to reset the network via the server with the updown commands for em1.
I then find that I am able to get a connection.
Now I know very little about networks, but it seems that the network is periodically dropping the server as opposed to the 14.04 dropping the network.
Below is the syslog file.

I believe the error occurs here:
[B][86660.970722] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[86666.934553] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[86666.934563] , receive & transmit flow control ON
[86666.934660] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready[/B][/B]
[/B]

Ideas? As to what may be taking place.
I really need this machine up and to have stable connectivity but I am actually unsure as to how to investigate this further.

Full output below.
-------------------------------------------
```


[    6.927451] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.1/2-1.4.1:1.1/input/input3
[    6.927548] hid-generic 0003:413C:2006.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.0-1.4.1/input1
[    8.320626] random: nonblocking pool is initialized
[    8.869340] systemd-udevd[209]: renamed network interface eth0 to em1
[    9.017376] systemd-udevd[205]: renamed network interface eth1 to em2
[    9.018303] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    9.018304] EXT4-fs (sda1): write access will be enabled during recovery
[    9.053033] EXT4-fs (sda1): orphan cleanup on readonly fs
[    9.053071] EXT4-fs (sda1): 6 orphan inodes deleted
[    9.053071] EXT4-fs (sda1): recovery complete
[    9.053819] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.493603] init: plymouth-upstart-bridge main process (265) terminated with status 1
[   10.560581] init: plymouth-upstart-bridge main process ended, respawning
[   10.638151] init: plymouth-upstart-bridge main process (275) terminated with status 1
[   10.701841] init: plymouth-upstart-bridge main process ended, respawning
[   10.771813] init: plymouth-upstart-bridge main process (279) terminated with status 1
[   10.835480] init: plymouth-upstart-bridge main process ended, respawning
[   11.901917] ERST: NVRAM ERST Log Address Range not implemented yet.
[   11.975756] Adding 31264764k swap on /dev/sda4.  Priority:-1 extents:1 across:31264764k FS
[   12.075689] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[   12.075702] IPv6: ADDRCONF(NETDEV_UP): em2: link is not ready
[   12.169274] systemd-udevd[389]: starting version 204
[   12.250737] lp: driver loaded but no devices found
[   12.258825] ACPI Error: SMBus/IPMI/GenericSerialBus write requires Buffer of length 66, found length 32 (20131115/exfield-299)
[   12.258840] ACPI Error: Method parse/execution failed [\_SB_.PMI0._GHL] (Node ffff880429141c58), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   12.258862] ACPI Error: Method parse/execution failed [\_SB_.PMI0._PMC] (Node ffff880429141bb8), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   12.258883] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMC (20131115/power_meter-756)
[   12.270476] IPMI System Interface driver.
[   12.270541] ipmi_si: probing via SMBIOS
[   12.270547] ipmi_si: SMBIOS: io 0xca8 regsize 1 spacing 4 irq 0
[   12.270550] ipmi_si: Adding SMBIOS-specified kcs state machine
[   12.270557] ipmi_si: Trying SMBIOS-specified kcs state machine at i/o address 0xca8, slave address 0x20, irq 0
[   12.329584] EDAC MC: Ver: 3.0.0
[   12.334544] EDAC MC0: Giving out device to module i7core_edac.c controller i7 core #0: DEV 0000:ff:03.0 (POLLED)
[   12.334653] EDAC PCI0: Giving out device to module i7core_edac controller EDAC PCI controller: DEV 0000:ff:03.0 (POLLED)
[   12.334824] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[   12.338059] type=1400 audit(1409839637.983:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=444 comm="apparmor_parser"
[   12.338075] type=1400 audit(1409839637.983:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=444 comm="apparmor_parser"
[   12.338087] type=1400 audit(1409839637.983:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=444 comm="apparmor_parser"
[   12.338996] type=1400 audit(1409839637.983:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=444 comm="apparmor_parser"
[   12.339010] type=1400 audit(1409839637.983:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=444 comm="apparmor_parser"
[   12.339547] type=1400 audit(1409839637.983:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=444 comm="apparmor_parser"
[   12.341489] type=1400 audit(1409839637.987:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=443 comm="apparmor_parser"
[   12.341500] type=1400 audit(1409839637.987:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=443 comm="apparmor_parser"
[   12.341509] type=1400 audit(1409839637.987:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   12.390972] kvm: disabled by bios
[   12.420663] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.429809] kvm: disabled by bios
[   12.493570] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.512847] bnx2 0000:02:00.0: irq 51 for MSI/MSI-X
[   12.512868] bnx2 0000:02:00.0: irq 52 for MSI/MSI-X
[   12.512888] bnx2 0000:02:00.0: irq 53 for MSI/MSI-X
[   12.512907] bnx2 0000:02:00.0: irq 54 for MSI/MSI-X
[   12.512927] bnx2 0000:02:00.0: irq 55 for MSI/MSI-X
[   12.512947] bnx2 0000:02:00.0: irq 56 for MSI/MSI-X
[   12.512967] bnx2 0000:02:00.0: irq 57 for MSI/MSI-X
[   12.512986] bnx2 0000:02:00.0: irq 58 for MSI/MSI-X
[   12.513005] bnx2 0000:02:00.0: irq 59 for MSI/MSI-X
[   12.537941] gpio_ich: GPIO from 180 to 255 on gpio_ich
[   12.542737] ipmi_si ipmi_si.0: Found new BMC (man_id: 0x0002a2, prod_id: 0x0100, dev_id: 0x20)
[   12.542756] ipmi_si ipmi_si.0: IPMI kcs interface initialized
[   12.578529] bnx2 0000:02:00.0 em1: using MSIX
[   12.578922] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[   12.586305] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   12.796241] init: udev-fallback-graphics main process (577) terminated with status 1
[   13.229363] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
[   13.242821] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[   13.421233] init: failsafe main process (797) killed by TERM signal
[   16.086674] init: plymouth-upstart-bridge main process ended, respawning
[   18.730753] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[   18.730764] , receive & transmit flow control ON
[   18.730864] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[86660.907789] bnx2 0000:02:00.0: irq 51 for MSI/MSI-X
[86660.907807] bnx2 0000:02:00.0: irq 52 for MSI/MSI-X
[86660.907822] bnx2 0000:02:00.0: irq 53 for MSI/MSI-X
[86660.907837] bnx2 0000:02:00.0: irq 54 for MSI/MSI-X
[86660.907851] bnx2 0000:02:00.0: irq 55 for MSI/MSI-X
[86660.907865] bnx2 0000:02:00.0: irq 56 for MSI/MSI-X
[86660.907880] bnx2 0000:02:00.0: irq 57 for MSI/MSI-X
[86660.907894] bnx2 0000:02:00.0: irq 58 for MSI/MSI-X
[86660.907908] bnx2 0000:02:00.0: irq 59 for MSI/MSI-X
[86660.970596] bnx2 0000:02:00.0 em1: using MSIX
[86660.970722] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[86666.934553] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[86666.934563] , receive & transmit flow control ON
[86666.934660] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[103496.833201] init: irqbalance main process (1025) killed by TERM signal
[104225.921977] bnx2 0000:02:00.0: irq 51 for MSI/MSI-X
[104225.921995] bnx2 0000:02:00.0: irq 52 for MSI/MSI-X
[104225.922010] bnx2 0000:02:00.0: irq 53 for MSI/MSI-X
[104225.922025] bnx2 0000:02:00.0: irq 54 for MSI/MSI-X
[104225.922039] bnx2 0000:02:00.0: irq 55 for MSI/MSI-X
[104225.922053] bnx2 0000:02:00.0: irq 56 for MSI/MSI-X
[104225.922067] bnx2 0000:02:00.0: irq 57 for MSI/MSI-X
[104225.922082] bnx2 0000:02:00.0: irq 58 for MSI/MSI-X
[104225.922096] bnx2 0000:02:00.0: irq 59 for MSI/MSI-X
[104225.985965] bnx2 0000:02:00.0 em1: using MSIX
[104225.986073] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[104231.945777] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[104231.945786] , receive & transmit flow control ON
[104231.945889] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[112396.576671] perf samples too long (2551 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[432402.213090] bnx2 0000:02:00.0: irq 51 for MSI/MSI-X
[432402.213108] bnx2 0000:02:00.0: irq 52 for MSI/MSI-X
[432402.213123] bnx2 0000:02:00.0: irq 53 for MSI/MSI-X
[432402.213138] bnx2 0000:02:00.0: irq 54 for MSI/MSI-X
[432402.213152] bnx2 0000:02:00.0: irq 55 for MSI/MSI-X
[432402.213166] bnx2 0000:02:00.0: irq 56 for MSI/MSI-X
[432402.213181] bnx2 0000:02:00.0: irq 57 for MSI/MSI-X
[432402.213195] bnx2 0000:02:00.0: irq 58 for MSI/MSI-X
[432402.213209] bnx2 0000:02:00.0: irq 59 for MSI/MSI-X
[432402.276994] bnx2 0000:02:00.0 em1: using MSIX
[432402.277250] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[432408.032804] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[432408.032814] , receive & transmit flow control ON
[432408.032911] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[610066.592610] bnx2 0000:02:00.0: irq 51 for MSI/MSI-X
[610066.592629] bnx2 0000:02:00.0: irq 52 for MSI/MSI-X
[610066.592644] bnx2 0000:02:00.0: irq 53 for MSI/MSI-X
[610066.592658] bnx2 0000:02:00.0: irq 54 for MSI/MSI-X
[610066.592672] bnx2 0000:02:00.0: irq 55 for MSI/MSI-X
[610066.592686] bnx2 0000:02:00.0: irq 56 for MSI/MSI-X
[610066.592700] bnx2 0000:02:00.0: irq 57 for MSI/MSI-X
[610066.592714] bnx2 0000:02:00.0: irq 58 for MSI/MSI-X
[610066.592728] bnx2 0000:02:00.0: irq 59 for MSI/MSI-X
[610066.656440] bnx2 0000:02:00.0 em1: using MSIX
[610066.656548] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[610072.516682] bnx2 0000:02:00.0 em1: NIC Copper Link is Up, 1000 Mbps full duplex
[610072.516693] , receive & transmit flow control ON
[610072.516789] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready

```

---

### Post by varunendra on 2014-09-14
Please try the only parameter available for the driver -
```
sudo modprobe -rv bnx2
sudo modprobe -v bnx2 disable_msi=1
```
Will be a temporary change that will be lost at next boot. If it helps we can make it permanent. If not, please check if your version has included any new parameters we can try -
```
modinfo bnx2
```

**PS:**
It is hard to believe that you don't already know it, but terminal outputs should always be posted within 'Code' tags. If you really don't know how to use it, please follow the link in my signature below. :p

---

### Post by buntu_hugenewbie11 on 2014-09-15
I tried the commands and as of now the server is up. 
But I can usually have it up for a few hours.
When running the modinfo bnx2 I received the output that is attached in the image.
[https://www.dropbox.com/s/ohg990mxajauxad/2014-09-15%2015.11.16.jpg](https://www.dropbox.com/s/ohg990mxajauxad/2014-09-15%2015.11.16.jpg)

---

### Post by buntu_hugenewbie11 on 2014-09-15
I am not at the server but in trying to ping it I find that is once again down.
What should I be looking for in terms of the root of this problem?
I will be able to do it in the morning.
Thanks for the help thus far.

---

### Post by varunendra on 2014-09-16
> **buntu_hugenewbie11 said:**
> What should I be looking for in terms of the root of this problem?
Anything in the logs (/var/log directory) that refers to networking and related stuff. I would personally look at dropped packets in ifconfig (are they unusually large in numbers?), and hints in /var/log/syslog.

Frankly, with the current amount of info, I can't even guess precisely where to look for further hints.

---

### Post by tgalati4 on 2014-09-16
This is troubling:

> IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready 

I presume that this server has 2 on-board ethernet ports.  It's possible that the ethernet chipset has worn out.  It gets hot (it's running at 1 gigahertz all of the time) and loses power and then you get *link not ready* in your log files.  Put your finger on the chipset (there should be 2 of them) and see how hot it is.  

Check and reseat your cabling.  Test your cabling for correct crimping and find a cable analyzer to give you a frequency response.  Most hardware expect perfect cabling and will degrade performance with poor cabling.  A shorted cable or a failing PoE (power over ethernet) port can cause problems.  

Switch to the second ethernet jack on the server, change ports on the switch, and watch your log files.  Using what you provided:

> tgalati4@Mint14-Extensa /tmp $ grep link network_issue.log 
[   12.075689] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[   12.075702] IPv6: ADDRCONF(NETDEV_UP): em2: link is not ready
[   12.578922] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[   18.730864] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[86660.970722] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[86666.934660] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[104225.986073] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[104231.945889] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[432402.277250] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[432408.032911] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[610066.656548] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[610072.516789] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready

There seems to be a 6-second reset period for the LAN device *em1* to become available again.  Do all of these resets correspond to resetting your switch?

In the future:

```
grep link /var/log/syslog
```

---

### Post by milos-rajsic on 2014-09-16
Proceed as @tgalati4 told.

But if in hurry always have an 1GB PCI ethernet card (10 Eur) spare and use it for emergency situations.

---

### Post by buntu_hugenewbie11 on 2014-09-29
Okay. I will look into the ethernet card.
There are 2 cards.
But the weird part is that if I reset the network using 
```
 ifdown em1 && sudo ifup em1 
```
 for the adapter then the network is up right away.
I get no errors that the adapter is down.
I spoke with the institution networking and they have nothing.
One technician believes it maybe because they have VOIP set-up over the network but I am not sure how that would affect things.
I will look into the overheating.
Thanks for the response.

---

### Post by buntu_hugenewbie11 on 2014-09-30
There seems to be no overheating issue.
So in looking at [code] grep link /var/log/syslog [\code]
I get the following messages when the connection is down.
[https://www.dropbox.com/s/lgof1ozp41pwz88/2014-09-30%2008.26.44.jpg]("https://www.dropbox.com/s/lgof1ozp41pwz88/2014-09-30%2008.26.44.jpg")
Sorry about the picture but it was the only way to quickly post.
Also the number of dropped RX packets is 102345. Tottal RX packets is 2071099.

I am not sure where else to go with this now.
\

---

### Post by tgalati4 on 2014-09-30
5% dropped packets seems high.  I get 0.5% dropped packets in an amusement park with a heavy network load and lots of outdoor connections.  

Try plugging in a pcie network card and use that for a while.  Also check the BIOS version and make sure it is the latest from Dell.  Upgrade the BIOS if you need to.

What is the condition of the cabling between the server and the switch?  Did you try changing the patch cord if they are in the same room?  If not in the same room, has someone shot a nail through your cable?  A shorted cable would cause an ethernet card to constantly reset itself.

If you get the same behavior between em1 and em2 by switching ports, then I would suspect the cabling or the switch.  How old is the switch?

---

### Post by buntu_hugenewbie11 on 2014-10-02
So the firewall engineers have said that they have security in place for "man in the middle" attacks.
Supposedly that may be affecting things but I don't know.
It seems too strange that I lose the connection at almost the same time.
I have checked the card and now the ip is bound to the mac but for some reason the loss is still occurring.
I will update if we learn more.
Given that the server has a dual link card. Could this be a possible reason for the lost connection?
How can I track what error occurs from the server side once the connection is lost?

---

### Post by Jonny87 on 2014-10-04
I'm having a similar issue to this with my ubuntu server 14.04, except I don't think its every 12 hours, it seems to be more random.

It usually has no monitor attached so I access it via ssh, but this becomes hard when I can't connect. I usually have to reboot the server and all is fine again untill it next drops out. I don't belive it's hardware as I'm confident that the hadware is fine. 

Server is serving samba and owncloud.

I'll keep watching this thread to see if it gets solved.

---

### Post by Jonny87 on 2014-10-05
OK I have something else to add, and wondering if it will be the same in the case of [COLOR=#000000]buntu_hugenewbie11 [/COLOR]if you can perhaps try it (if it's possible) the next time you have a drop out.
I have now attached a monitor to my server until I get this fixed. And today I went to access a share (knowing that I had access just earlier in the day) and it wouldn't let me. Couldn't even ssh to it. So I went to the keyboard for the Server and sent a ping to the desktop I was trying to access it from. The ping came back with a reply straight away. I then went back to the desktop and I had access to the server. It's like the out going ping reactivated the network connection or something. I'm not sure if this brings me any closer to the problem but thought I share it in case it gives someone an idea.

---

### Post by buntu_hugenewbie11 on 2014-11-01
So I found out that it was because of the following iThe Dell T310 comes with an iDRAC module as well and should have openmanage installed upon it.

Our it security people were worried about man-in-middle attacks and were blocking the connection when this different mac address was found I guess.
They were finding that iDRAC attempting to obtain a DHCP address, using the same port.
Either way since being informing them of this extra mac, I have not had an issue with the server going down.
We also have Cisco VOIP going over the same ports so that may have been an issue as well.

---

### Post by praseodym on 2014-11-02
Hi,

how do you connect? Via router? Does the router setting request a new IP of your ISP every 12 hours? Tried to deactivate IPv6 system-wide?

Add these lines to /etc/sysctl.conf and reboot.
```

net.ipv6.conf.all.disable_ipv6=1  
net.ipv6.conf.default.disable_ipv6=1  
net.ipv6.conf.lo.disable_ipv6=1
```

---

