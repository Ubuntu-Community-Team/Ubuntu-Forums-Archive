---
title: "Two Ethernet Ports - Swap/Disappear"
date: 2020-06-22
forum: Networking &amp; Wireless
---

### Post by jphat on 2020-06-22
Hi All

I'm running Ubuntu 20.04 LTS on a old server board S1200BTL as a home server.  The motherboard has two ethernet ports.  I connect to my LAN via a B525 Huawei wireless router.  The home server is hard wired to the wireless router via the ethernet port.

My problem is that after a restart or startup the ethernet port sometimes disappears so that to get it to re-appear I must then unplug the ethernet cable from the one port on the server and plug it into the other.  Then the network re-appears.  This manual swapping of the ports is a real pain as the PC is not super accessible.

Any ideas as to why it swaps or how if it does keep swapping I can get both to be automatically enabled?

Forgot to say I have eth0 and eno1 showing and ethernet controllers are Intel 82579LM and 82574L.

Thanks in advance.

---

### Post by TheFu on 2020-06-22
DHCP or static IPs specified on the system using netplan?
The DHCP server may be slow.
The router port many be starting to fail.
The ethernet cable may be starting to fail.
The ethernet ports on the "old server" may be starting to fail and jiggling the connection is sufficient.
Systemd-Networking may not be configured correctly.

I have a Debian virtual machine that sometimes doesn't find any network adapter at boot, but once it does, it is up until I have to bring the VM down. Then it is a 50:50 chance at the next boot whether the virtio NIC will be found or not.  The host machine doesn't have any network issues.  The other VMs on the system don't have any issues with networking at boot either, using the same driver and same bridge connection.

To see the boot messages:
```
$ dmesg |grep eth
[    0.910969] virtio_net virtio0 ens3: renamed from eth0
```
May need to tweak the regex (eth) a little for your setup.

---

### Post by chili555 on 2020-06-22
```
DHCP or static IPs specified on the system using netplan?
```We hope so. If hat is the case, Mr. TheFu and I will like to see the file:

```
cat /etc/netplan/*.yaml
```

---

### Post by jphat on 2020-06-23
Thanks for the assistance; in the first:

dmesg |grep eth
[    0.861792] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1e:67:1a:23:61
[    0.861793] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.861830] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 0100FF-0FF
[    0.984225] e1000e 0000:02:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:1e:67:1a:23:60
[    0.984226] e1000e 0000:02:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    0.984314] e1000e 0000:02:00.0 eth1: MAC: 3, PHY: 8, PBA No: 1000FF-0FF
[    0.985150] e1000e 0000:00:19.0 eno1: renamed from eth0

Then, 
cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

---

### Post by TheFu on 2020-06-23
> **jphat said:**
> Thanks for the assistance; in the first:

dmesg |grep eth
[    0.861792] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1e:67:1a:23:61
[    0.861793] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.861830] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 0100FF-0FF
[    0.984225] e1000e 0000:02:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:1e:67:1a:23:60
[    0.984226] e1000e 0000:02:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    0.984314] e1000e 0000:02:00.0 eth1: MAC: 3, PHY: 8, PBA No: 1000FF-0FF
[    0.985150] e1000e 0000:00:19.0 eno1: renamed from eth0

Then, 
cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

Netplan YAML files are indentation specific.  When posting here, you ABSOLUTELY MUST use code tags for any YAML file configurations. There's no other option.  The "advanced editor" has a '#' button to be used just like a quote or bold ... Wrap the YAML in that or we'll have to assume bad formatting.

If this is a server install, then network-manager is useless.  On a desktop, perhaps you can do something through a GUI?
If it was me, I'd not use network manager on any server. You can configure the static IP for the NIC you want in a netplan yaml file. 
Something like this:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "172.22.22.80", "1.1.1.1" ]
                search: []
```
Obviously, replace the values above for your needs.  IP, netmask, gateway and your internal DNS server are probably best.  Be certain that whatever IP you choose on the network is outside the DHCP managed range. On my network, I've setup 200-254 as DHCP managed. .199 and lower are for static IPs. Every network is different. 

Watch the spacing and indentation. If they are wrong, it won't work.  

I'd create+edit a file using **sudoedit /etc/netplan/01-eth0-static.yaml**, then run 
```
sudo netplan generate
sudo netplan apply --debug

``` to get it enabled. 

If you need help with specific values, most your modifications.

---

### Post by jphat on 2020-06-24
Sorry about the code tags.  A bit of fiddling with the yaml file (new to me) seems to be working for now.  I set eth1 and eno1 the same.
```
:~$ cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      addresses:
        - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]
    eno1:
      addresses:
        - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]

```
All good?  Thanks for the help.
Josh

---

### Post by TheFu on 2020-06-24
No. You cannot have 2 NICs on the same IP.  Actually, having 2 NICs on the same subnet is a bad idea when you don't understand networking. Problems will happen. Best to NOT setup eno1 at all.

And the comment in the 1st line isn't true anymore. Delete it.

---

### Post by The Cog on 2020-06-24
As I understand it, only one NIC is plugged in. It's just that their IDs keep swapping when it reboots. The original question was how to prevent them from swapping so that the same physical port always gets the same name. 

This page [https://netplan.io/examples](https://netplan.io/examples) has an example which has a match macaddress clause which might work. But I can't help feeling that there must be a lower-level way of pinning the interface names.

---

### Post by TheFu on 2020-06-24
Technically, it is possible to have NICs on the same subnet. People do that for automatic failover using cluster software and virtual IPs. They also do that for bonded connections, but the switch(es) they connect into need to support those protocols. Average home routers do not. A "managed switch" is usually required at the minimum with the specific ports spelled out.  The metric for each interface needs to be set correctly too.

As shown above, problems are likely due to the settings.  [https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629](https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629) has a bonded network setup, but it is for a KVM host and bridge on a network infrastructure that supports bonding.

---

### Post by jphat on 2020-06-24
I was unsure if I could use the same 2 IP addresses on the two NICs.  I tried editing the yaml file so one was 192.168.8.99 and the other 192.168.8.100 (both outside the range served by the router).  It didn't work. Both ways with the file (same and different IPs) as it was it only seems to connect eno1 and never eth1.

My intention is that I avoid the adapters swapping at random so that it's always on but also that either adapter will always work so that if the server cable is unplugged and plugged in again but in the other port (such as would happen in the house where some other family member moves things around) it still connects without any other fiddling.

What do you mean by: "And the comment in the 1st line isn't true anymore. Delete it." If you mean the:
# Let NetworkManager manage all devices on this system
line then I though networkmanager is managing as it is listed under renderer: NetworkManager

---

### Post by TheFu on 2020-06-24
> **jphat said:**
>  
What do you mean by: "And the comment in the 1st line isn't true anymore. Delete it." If you mean the:
# Let NetworkManager manage all devices on this system
line then I though networkmanager is managing as it is listed under renderer: NetworkManager

I missed that you left NM in there. That file was written for networkd.  NM doesn't handle non-trivial situations well at all.  I wouldn't be surprised to find that NM is the core of the problem. Were it me, I'd use networkd and only configure 1 of the ports. Bet that will solve it.

---

### Post by jphat on 2020-06-25
I changed it to networkd in the yaml file.  The port eno1 seems to consistently work but the other physical port (eth1 I assume) doesn't seem to do anything.
```
:~$ cat /etc/netplan/*.yaml
# Let Networkd manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 192.168.8.99/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]
    eno1:
      addresses:
        - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]

```

---

### Post by TheFu on 2020-06-25
You need to prioritize the connections, using the "_metric_".  Look at the routing table. Don't leave the NICs with the same metric.

---

### Post by jphat on 2020-06-25
I looked up routing table to find this phantom "metric".   I only see eno1 displayed??
```
:~$ sudo route -n
[sudo] password for joshua: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    0      0        0 eno1
192.168.8.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
```

---

### Post by TheFu on 2020-06-25
"accidentally" connect both ethernet ports and look again.

---

### Post by jphat on 2020-06-25
If I unplug the cable from the one port and into the next then I'm disconnected from the network and the routing table is blank.

Do you mean I must get another cable and plug both ports into the router simultaneously?

---

### Post by TheFu on 2020-06-25
> **jphat said:**
> If I unplug the cable from the one port and into the next then I'm disconnected from the network and the routing table is blank.

Do you mean I must get another cable and plug both ports into the router simultaneously?

Must? No. You don't need to do anything.  If it is impossible for someone to accidentally plug in 2 cables, then I wouldn't bother.  I certainly wouldn't go buy anything.  

Only you know what makes sense.

---

### Post by jphat on 2020-06-26
They can't plug in two at once but they can plug into a port which may or may not work.

---

### Post by TheFu on 2020-06-26
> **jphat said:**
> They can't plug in two at once but they can plug into a port which may or may not work.

Is the reason they cannot plug 2 in at once just because there's only 1 cable in the location?  If so, that's fine.
Why not just block the plug you don't want them to use?  I'd take a broken RJ45 cable, cut it down to 1 inch and put it into the port you don't want available.  Simple solution.  I think an old telephone rj11 should fit and click into the plug too.

---

### Post by jphat on 2020-06-26
That'll work provided the ports don't take to swapping themselves from  time to time.  Do you think the current setup has corrected that?

---

### Post by TheFu on 2020-06-26
> **jphat said:**
> That'll work provided the ports don't take to swapping themselves from  time to time.  Do you think the current setup has corrected that?

Anything that removes network-manager is a step up in my book,, but i've never tested anything like what you are doing.  Most places, specific ports are connected to specific networks.  I’ve never seen swapping.  Networking doesn't do that when we set it up using server methods.

But no way to know until you test.

---

### Post by jdally987 on 2020-07-01
Just out of curiosity, how long has it been doing the swapping thing for you? Was there a period before that where it didn’t do that?

---

### Post by jphat on 2020-08-24
Since install of Ubuntu.  It still swaps from time to time which is a real pain when I'm not in then someone in the family will be moaning about the crappy server.

---

### Post by jphat on 2021-01-30
Hi All

Hoping there's some new blood out there who'll have a stab at my ever present networking problem.  

As background I'm running an old server (Intel S1200BTL) as a home server - normal ubuntu 20.04.01 LTS with gui for the tech challenged.

It has two ethernet ports.  The server is not always on as it's used as a data store, so is not always needed. Other devices in the house are Windows 10 pcs and Android phones.

The server has a static IP address and is plugged into the wireless router via ethernet cable.  The wireless router is operating as the dhpc server.

On startup the server seems to randomly pick which of the 2 mobo ethernet ports it feels like using, with the result that sometimes it can connect via the router and sometimes it can't.  Every time I restart the server I therefore first open a browser to see if I can access the internet.  If I can't then I hot pull the network cable on the mobo out the one port and stick it in the other - no restart required and then the server will see the internet.

Why does the server randomly swap between the two ports and how do I stop it?

As an aside, the other devices (pcs and phones) can only see the server if it was started first, otherwise I need to restart the devices (once I know the server can see the internet) after I have started the server.

Thanks,

Josh

---

### Post by The Cog on 2021-01-30
A basic question: Is it the ID (eth0 vs en0) that moves from one port to the other? So that for instance, the working interface is always eth0 or always en0 regardless of which port that is. 
Or does the working interface change, sometimes eth0 works and sometimes en0 works?

Capturing the output of **ip address** both before and after you move the cable would be very informative.

---

### Post by jphat on 2021-01-30
It varies between eth1 and eno1.

Currently it's on eno1 (for future reference, for myself that's physically the lower port on the box).
> ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:61 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:60 brd ff:ff:ff:ff:ff:ff


---

### Post by The Cog on 2021-01-30
That's a good start. It will be interesting to see if the names swap ports when you have trouble - you will be able to check because the MAC address will definitely stay with the port. 
I would prefer to see the output of ip address though, because then we will be able to see if it's a problem with DHCP, if the interface shows LOWER_UP but no IP address.
Another possibility is that the interface the cable is plugged into still shows NO-CARRIER meaning it hasn't detected the cable for some reason.

---

### Post by jphat on 2021-02-01
not sure if this helps (the ip address is set to 192.168.8.100, it restarted today with no issues (as I said it seems random):
>  ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.100  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::21e:67ff:fe1a:2361  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:67:1a:23:61  txqueuelen 1000  (Ethernet)
        RX packets 5864  bytes 5612651 (5.6 MB)
        RX errors 0  dropped 209  overruns 0  frame 0
        TX packets 4538  bytes 542879 (542.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  memory 0xc1a00000-c1a20000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 559  bytes 69469 (69.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 559  bytes 69469 (69.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


---

### Post by The Cog on 2021-02-01
Well, they didn't swap identities this time, and DHCP worked. I guess we have to wait until it gives us a clue.

Your posts would look better if you use code tags instead of quote. If you click Go Advanced, there is a # button that works like quote but adds code tags instead.

---

### Post by jphat on 2021-02-03
OK, swapped again this morning. I see it is staying eno1 (perhaps I was mistaken about swapping between eth1 and eno1)(now plugged in upper port). 

Strangely mac addresses swapped, and the list order swapped.
> ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:61 brd ff:ff:ff:ff:ff:ff
3: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:60 brd ff:ff:ff:ff:ff:ff


And:
>  ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.100  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::21e:67ff:fe1a:2360  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:67:1a:23:60  txqueuelen 1000  (Ethernet)
        RX packets 2553  bytes 1492282 (1.4 MB)
        RX errors 0  dropped 199  overruns 0  frame 0
        TX packets 2213  bytes 347415 (347.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xc1900000-c1920000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13222  bytes 990952 (990.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13222  bytes 990952 (990.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



---

### Post by jphat on 2021-02-03
Had to restart for a software update - ports swapped again requiring unplugging and changing physical port again.

Not sure what it means but in addition to mac address swapping around connection which works is always eno1 and I see the other is either eth0 or eth1.

---

### Post by jphat on 2021-02-03
Had to restart for a software update - ports swapped again requiring unplugging and changing physical port again.

Not sure what it means but in addition to mac address swapping around connection which works is always eno1 and I see the other is either eth0 or eth1.

---

### Post by The Cog on 2021-02-03
OK, that's progress. We know that the ethernet ports are switching names. I think this is because hardware discovery is done in parallel, and so hardware is not always discovered (and named) in the same order. A change in Ubuntu a couple of years ago was intended to fix that problem. In the process, all the interface names changed so that eth0 etc no longer existed. Instead they get rather odd names that incorporate the hardware bus numbers etc, but it means that a name always means exactly the same interface, every reboot.

It seems that your PC doesn't assign those hardware-dependent names. I think the hardware dependent naming can be disabled by creating a file /etc/udev/rules.d/80-net-setup-link.rules (the contents are irrelevant). It may be worth looking for this file and deleting it if present. Then edit your interface config to match the new name. It should no longer swap.

There are probably other ways to solve this problem, but I don't know what they are. Maybe add a MAC address definition to the interfaces config?

---

### Post by jphat on 2021-02-04
Hi

I don't seem to have the 80-net-setup-link.rules file.

I opened the interfaces file under /etc/network and it's populated with:

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by The Cog on 2021-02-04
I think I'm out of my depth  now. I don't understand why they are not getting allocated the hardware-based names (even Ubuntu 18.04 does that - the laptop I'm on right now has an interface enp0s31f6).
And I don't know why DHCP seems not to work on the other interface. Is there anything in /etc/NetworkManager that might differentiate between the interfaces?

---

### Post by jphat on 2021-02-05
If I open the NetowrkManager.conf it says the following:
> [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

Hope that's helpful?

---

### Post by jphat on 2022-01-16
Same problem still exists, no ideas out there?

---

### Post by alexleo007 on 2022-05-17
At my workplace we constantly use this intel s1200btl boards and came across this issue. Some SuperMicro boards exhibit same issue.

It has to do with both NICs, sitting on the same PCIe Bus. It's a systemd bug, you'll find same issue occurs on CentOS and Redhat systems

There are 2 ways to configure:

[COLOR=#333333][FONT=&amp]**Method 1**[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Create a file at */etc/udev/rules.d/70-persistent-net.rules* and list both devices with new name Example, *NAME=""* can be anything you want, eth1, enp5, whatever. *ATTR{address}==""* has to be the NIC's MAC address, you can see it by using ifconfig and checking out HWaddr label[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]```
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:67:46:3f:ef", ATTR{dev_id}=="0x0", ATTR{type}=="1", NAME="eno1"
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:67:46:3f:ee", ATTR{dev_id}=="0x0", ATTR{type}=="1", NAME="eth0"
```[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Reboot and check if the NICs have names you specified above.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Proceed normally as you would with editing interfaces file with the name you chose above.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]**Method 2**[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Edit your /etc/default/grub changing the line to[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]```
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
```[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]From [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]```
GRUB_CMDLINE_LINUX=""
```[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Do [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]```
$ sudo update-grub
```[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Then reboot. Now it should use old convention for naming NICs, eth0, eth1, etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]

Sources: [/FONT][/COLOR]https://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04/801310
[https://www.centos.org/forums/viewtopic.php?t=54945](https://www.centos.org/forums/viewtopic.php?t=54945)

---

### Post by jphat on 2022-07-27
Hi Alexleo007

Thanks very much for posting, I had given up on finding a solution and somehow never got an email notification when you posted.

My wife was complaining about the &%^*^$$ connection again so I happened to google it again and found my way back here.

I've tried method 2 as a one line edit to the grub file seems simpler for me - I'm no IT specialist.

I'll report back as to how it goes.

Thanks again!

---

### Post by jphat on 2022-07-27
The Method 2 from Alexleo007 resulted in the devices being renamed to "eth0" and "eth1" from "eth0" and "eno1".

```
joshua@zalman:~$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:61 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:1e:67:1a:23:60 brd ff:ff:ff:ff:ff:ff
```

Then nothing worked, I then edited the .yaml file to reflect the eth0 device as per:
```
# Let Networkd manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]
```

I'm guessing now it'll continue to work if the cable is not moved between physical ports.  If I change the ethernet cable to the other physical port, the port (eth1 I'm guessing) lights up but there's no connection.  This makes sense to me as only eth0 is dealt with in the .yaml file.

To get the other port to work as well, regardless of which port gets plugged in of the two, as in multiple devices and a single IP address (redundancy in devices), I assume I need to setup a bond or something in the .yaml file.

I tried but without success, I'm afraid it's above my pay grade.
I'd appreciate if someone could post the entries for the .yaml file for the 2 ethernet devices, eth0 and eth1 with a single ip address 192.68.8.100

Thanks in advance!

---

