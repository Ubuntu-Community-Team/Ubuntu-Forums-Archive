---
title: "Feisty Wireless stopped working out nowhere"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by jordanm on 2007-05-28
When I first installed Feisty on my Sony Vaio SZ laptop it worked flawlessly. Out of nowhere, it just stopped working though. Now when I try to use wireless it shows no networks available, and the system does not seems to even see my card for some odd reason.

When I do an 'lshw' it shows the card, so it obviously sees it:
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0
                resources: iomemory:dc100000-dc100fff irq:17


lsmod shows that the correct driver is loaded:
ipw3945               118816  0
ieee80211              34760  1 ipw3945


Yet ifconfig shows no card (it used to come up as eth1, eth0 is my wired ethernet which is currently plugged in):
eth0      Link encap:Ethernet  HWaddr 00:13:A9:3E:82:53 
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe3e:8253/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3721651 (3.5 MiB)  TX bytes:1083772 (1.0 MiB)
          Interrupt:18

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Iwconfig also shows nothing for eth1:
lo        no wireless extensions.

eth0      no wireless extensions.

/etc/iftab still shows it:
eth0 mac 00:13:a9:3e:82:53 arp 1
eth1 mac 00:13:02:bd:e8:17 arp 1

/etc/network/interfaces also does:
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth0


Finally, doing 'ifup eth1' gives:
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.


Anyone know what's going on? Its odd cause it worked fine until yesterday, then stopped worked. Last night it randomly started working again and then after reboot it no longer works again. Today I can't get it to work no mater how hard i try.

---

### Post by jordanm on 2007-05-28
Bump... I really need to get this figured out cause I can't afford the trouble of having to reinstall Feisty.

---

### Post by hurt on 2007-05-28
do u have a function button that disables wireless? cause i pressed it and well it is working now.

---

### Post by jordanm on 2007-05-29
The function button is enabled so it should work. So far I've tracked it to a conflict with various old /var/run/*,pid files which are not removed on shutdown, so therefore prevent new the program on boot (such as ipw3945). I'll post more here as I figure out in case anyone has the same problem in the future.

In the meantime, does anyone know if there a default ubuntu script that is supposed to clean out /var/run on reboot? It looks like bootclean is supposed to, but I can't find code in there that actually does. Worst case scenario, I'll do a 'rm -f /var/run/*' on init 0 and 6, but I'd rather find a nicer way to do it.

---

### Post by mlentink on 2007-05-29
Did you apply the latest kernel update yesterday?
That's what stopped my wifi card, with similar symptoms. I rolled back the kernel and now it works again...

---

### Post by hopestorm on 2007-05-29
How do you roll back?
I lost the wifi and there is no Ethernet to link. Is there a way to downgrade without internnet link?

---

### Post by mlentink on 2007-05-29
Reboot and press [Esc] when GRUB comes up. You can then select the previous kernel to boot

---

### Post by jordanm on 2007-05-29
Rolling back to the previous kernel did not fix my problem...

---

### Post by mlentink on 2007-05-29
Bummer.
It did mine. Sorry.

---

### Post by useResa on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117580](https://bugs.launchpad.net/ubuntu/+bug/117580) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **mlentink said:**
> Did you apply the latest kernel update yesterday?
That's what stopped my wifi card, with similar symptoms. I rolled back the kernel and now it works again...
I have encountered the same issue and reported it in the bug I found.
Maybe you could also report your issue?

---

### Post by webworldx on 2007-05-29
> **useResa said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117580](https://bugs.launchpad.net/ubuntu/+bug/117580) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				
I have encountered the same issue and reported it in the bug I found.
Maybe you could also report your issue?



My video card has also reverted back to Mesa after the kernel upgrade. Unfortunately booting to the previous kernel doesn't bring the wireless back, but does bring back my ATI card...

---

### Post by atte on 2007-09-03
For the Intel ipw3945, if your modules are loaded but you have no interface showing up, try to run /sbin/ipw3945* (something). I don't know exactly how it works but I think it loads binary stuff needed by the driver. Since that binary is version-specific it might be a good idea to see which one you have and give it a go. Worked for me! Good luck!

---

