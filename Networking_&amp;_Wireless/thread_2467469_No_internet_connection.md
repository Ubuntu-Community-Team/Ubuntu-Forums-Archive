---
title: "No internet connection"
date: 2021-09-27
forum: Networking &amp; Wireless
---

### Post by yoramdavid on 2021-09-27
Hello.
Internet was working fine, both wi-fi an Ethernet.
Then there was an update of snap and the next time I started the laptop, I could not connect to the internet, either wi-fi is Ethernet.
I tried to boot from a USB Kubuntu disk, same problem from the pen drive.

I already tried what is suggested in this website: [https://www.cyberithub.com/solved-no-internet-connection-after-installation-of-ubuntu-20-04/](https://www.cyberithub.com/solved-no-internet-connection-after-installation-of-ubuntu-20-04/)
Nothing changed.
I tried uninstalling snap, nothing changed.
When I run "ping google.com" in the terminal, I get the error "temporary failure in the resolution of the name" translated from Portuguese.

I am on Kubuntu 20.04
Network manager 1.22.10
Ethernet controller: realteck semiconductor
Network controller: Nvidia GM107M

Thank you for any help
Yoram

---

### Post by TheFu on 2021-09-28
DNS failing doesn't mean that the internet is down or your access is broke.  It just means that DNS isn't working.

See if you can ping a well-known IP - 
```
ping 8.8.8.8
```
Does that work? If it does, it is just a DNS issue, nothing more.
If that ping fails, try to ping your router.  I don't know the IP address, but 192.168.0.1 is common. You'll need to figure that out.

To get your configured gateway - usually your router, use:
```
read -r x x i x< <(ip r g 1);echo "$i"
```
Then try to ping the IP returned by that command. Or do it all in 1 command:
```
ping -c 2 $(read -r x x i x< <(ip r g 1);echo "$i")
```
If that works, then try rebooting the router and checking other systems on the LAN for issues.
If that doesn't work, we need some information about the network devices in your computer.  This is where it gets harder, since the easy ways to get that information are using tools that aren't installed by default - so if you haven't installed them, it will get ugly. Anyway, the easy commands are:
```
inxi -Nx
# or
lshw -C network
```
Either is fine.
If those say **Command not found,** or something like that, then we have to do it the harder way:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
#  or
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```
The last command is the most flexible, but getting the spacing correct is less easy.
From there, we can decide what to do.  Hopefully, the first *ping 8.8.8.8* command works. If so, stop and let us know that.

---

### Post by yoramdavid on 2021-09-28
Thank you for your help.
Nothing so far.
Ping 8.8.8.8 gave the following result:
<PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
1213 packets transmitted, 0 received, 100% packet loss, time 1241080ms>

ping 192.168.2.1 gave the following result:
<PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=3.81 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.02 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=1.04 ms
(...)
64 bytes from 192.168.2.1: icmp_seq=60 ttl=64 
64 bytes from 192.168.2.1: icmp_seq=110 ttl=64 time=1.37 ms
^C
--- 192.168.2.1 ping statistics ---
110 packets transmitted, 99 received, 10% packet loss, time 109344ms
rtt min/avg/max/mdev = 0.987/1.141/4.551/0.457 ms>

ping -c 2 $(read -r x x i x< <(ip r g 1);echo "$i") have the following result:

<code>PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.26 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.23 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.230/1.246/1.262/0.016 ms
yoram@yoram-portatil:~$ 
</code>

Rebooting the router did nothing.
My phone, from where I write this, connects well to the wi-fi and another laptop connects well with the LAN.

I will now try the next steps.
PS: sorry I don't know how to place the terminal results in a voice tag from the phone.

---

### Post by yoramdavid on 2021-09-28
Here we are:

~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 6b
       serial: 80:19:34:4c:5e:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.11.0-36-generic firmware=17.3216344376.0 7260-17.ucode ip=192.168.2.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:38 memory:f7900000-f7901fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 12
       serial: 78:24:af:c8:6a:91
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-36-generic duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.2.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813ff

---

### Post by TheFu on 2021-09-28
The commands you've run so far say the problem is between the router and the internet, not between the computer and the router.
Only enable the wired connection.
Or 
Only enable the wifi connection.
Never have both enabled concurrently.

The RTL8111/8168/8411 PCI Express Gigabit Ethernet is connecting to the router at only 100base-tx speeds. That usually doesn't make sense, unless your router is really, really, really, old or there is a bad cable.

I also see you are running kernel version 5.11.x ... which is really new.  There have been a number of network issues with that kernel. Can you run the 5.4.x kernel instead?  20.04 should still have that installed.  For non-LTS, newer, releases, I really cannot help.  I'm an LTS-only person.

If you haven't patched the router in the last 3 months, patch it.  If there aren't any patches available, it is time for a new router.  Routers need to be patched all the time.  I patch mine weekly.  Usually there are updates every other week as a reference.

---

### Post by yoramdavid on 2021-09-29
Well,
That explains that the internet came back as mysteriously as it went. I connected the computer today (after 3 days of no internet) and it was working!

I understand what you said, but it remains mysterious that other devices could connect to it while I could not.
Yes, I only have ehternet or wifi enabled at a time. Not both.

Well, all is well that ends well.
Thank you very much for your help.
Regards,
Yoram

---

