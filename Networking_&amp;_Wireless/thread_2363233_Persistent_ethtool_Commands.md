---
title: "Persistent ethtool Commands"
date: 2017-06-07
forum: Networking &amp; Wireless
---

### Post by anderbak on 2017-06-07
Hello all,

Ubuntu 16.04 (minimal)
[LIST]
[*]KVM + libvirt + virtinst
[*]samba
[*]ssh
[*]more later after basic setup
[/LIST]

network config
[LIST]
[*]enp6s0
[*]enp8s6 (Passed through to guest and not visible to host)
[*]br0 (bridged with enp6s0 for guest connectivity)
[*]vnet0 (virtual interface created by KVM for guest - pfSense in this case)
[/LIST]
 
```

anderbak@Server-Ubuntu:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 94:de:80:28:a9:dc
          inet addr:192.168.1.5  Bcast:192.168.255.0  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fe28:a9dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19265 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7154778 (7.1 MB)  TX bytes:96742 (96.7 KB)
enp6s0    Link encap:Ethernet  HWaddr 94:de:80:28:a9:dc
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21991 errors:0 dropped:2 overruns:0 frame:0
          TX packets:11783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6344386 (6.3 MB)  TX bytes:7573008 (7.5 MB)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:393804 (393.8 KB)  TX bytes:393804 (393.8 KB)
virbr0    Link encap:Ethernet  HWaddr 52:54:00:c0:14:1c
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
vnet0     Link encap:Ethernet  HWaddr fe:54:00:67:dc:b4
          inet6 addr: fe80::fc54:ff:fe67:dcb4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8043324 (8.0 MB)  TX bytes:1510231 (1.5 MB)
```

```
anderbak@Server-Ubuntu:~$ cat /etc/network/interfaces
source /etc/network/interfaces.d/*
auto lo enp6s0 br0
iface lo inet loopback
iface enp6s0 inet manual
iface br0 inet static
        network 192.168.1.0
        gateway 192.168.1.1
        address 192.168.1.5
        broadcast 192.168.255
        netmask 255.255.255.0
        dns-nameservers 192.168.1.1 208.67.222.222 208.67.220.220
        bridge_ports enp6s0
```

In order for pfSense (and the network behind it) to function in this manner, tx checksum offloading must be disabled on vnet0 (guest adapter), which is easily accomplished using ```
# ethtool -K vnet0 tx off
``` Unfortunately, my google-fu skills haven't led me to any *Ubuntu *related scenarios where ethtool commands are issued when or after libvirt/qemu creates an interface. The closest I've come are using rc.local to issue the command while Ubuntu is loading (when the interface doesn't yet exist) and a CentOS resolution that looked promising which uses an ifup-post script that, afaik, doesn't exist on Ubuntu.

**How can an ethtool command be automated for only vnet0 after libvirt/qemu has created the interface?**

If there are any other glaring mistakes, feel free to tell me - I don't pretend to be an expert in any of this.

---

### Post by TheFu on 2017-06-07
The interface file supports pre-up and post-up stanzas.  The manpage for 'interfaces' has complete details.

---

### Post by anderbak on 2017-06-07
> **TheFu said:**
> The interface file supports pre-up and post-up stanzas.  The manpage for 'interfaces' has complete details.

Is this something that can be done with an interface that is created dynamically by libvirt? i.e. vnet0, vnet1, etc. where the vnetX is associated to a corresponding libvirt guest? I had seen examples of this done for interfaces that could be defined in /etc/network/interfaces, but vnet0 (the particular interface of interest) is defined elsewhere.

I'm currently reading the manpage to gain a better understanding.

---

### Post by TheFu on 2017-06-08
libvirt interfaces didn't work well in the beginning, so people doing virtualization for a long time don't use them. We learned long ago to make our own bridges and have control over the networking in order to have extremely stable connections with excellent performance.

Don't know if that helps your situation. Sorry.

I run pfsense in a VM, but only for internal networking.  The edge router, facing the internet, runs pf on a dedicated piece of HW.  For us, it is a security thing.

---

### Post by anderbak on 2017-06-08
I agree with the performance benefits of creating my own bridge - I've actually already created my own bridge, br0, as I pointed out in my initial post. br0 is handling the traffic on the **LAN** side only. I also completely agree with the security risks of running pfSense in a VM _where the **WAN** interface is virtualized_, which is why I'm using IOMMU to pass the WAN interface directly to the guest. The first node packets inbound from the interwebs touch is natively located on pfSense - _not the host_. This way, I have the security of your pf edge router and the performance of your pf vm.

Is your virtualized pfSense running on KVM/Xen or another hypervisor? Having to use ethtool to turn off tx tcp checksums is specific to KVM/Xen and a[ known issue]("https://forum.pfsense.org/index.php?topic=88467.0"). I just haven't been able to find anywhere that explains how to automate the command.

---

### Post by TheFu on 2017-06-08
While passthru is the best option, it is still not enough, IMHO.  It doesn't pass my "smells-bad" test.  I won't allow the louder "it will work and be secure" guys from swaying my *BS-meter* for the true risks.  But, each org needs to figure that out themselves within their limitations.  We always hear that full virtualization is secure, yet white and black hats are breaking out of of VMs (all of them) into the hostOS all-the-time.  At my defcon group, we learn how to do it. Doesn't matter which hypervisor is used, but I would say this .... KVM *without QEMU* is likely the most secure. The proprietary hypervisors like to yell loudly. They shouldn't.  In most real-world installs, orgs are running extremely old versions, that haven't fixed the most recent issues.

Web-based password managers don't pass my smell test either, BTW. If you want something to be secure, you don't put it on the internet. Is that hard to understand?  I suppose if you are a typical home user, running an unpatched router, Windows (of any sort), with (or without) no security addons and like to surf dangerous websites, then a reputable cloud-based password manage MAY be more secure for you.  Not for anyone here.  It smells bad, right?  I know of only 1 thing in the last 25+ yrs that is actually more secure AND more convenient. ssh + ssh-keys. Every other claim of better security AND more conveniences fails.

I'm using KVM and don't recall anything special needed. Because it is LAN-only, I didn't use VT-d, but prevented the hostOS from using that NIC.  On my WAN-facing pf box, it definitely has HW accel on the NICs.  Before I enabled that, performance was only in the 650Mbps range.  

IMHO.

Gotta run. No time left today. sorry. Good luck.

---

### Post by anderbak on 2017-06-08
I can absolutely appreciate the sentiment regarding security - my degree is in Cyber Ops; although, I have 0 real world experience (otherwise employed). This machine is only a simple homebrew without the need to secure information of any real value and everything is backed up off site anyhow. That's not to say that I'm throwing caution to wind and don't care about security - the goal of this project is just to get all of my hardware in one box in order to improve the happy-wife factor.

> I'm using KVM and don't recall anything special needed. Because it is LAN-only, I didn't use VT-d, but prevented the hostOS from using that NIC.  On my WAN-facing pf box, it definitely has HW accel on the NICs.

This is interesting, because the only other difference that could remain is if you're not using the virtio drivers for your virtual interface or aren't running pfSense 2.2 or beyond (apparently it wasn't a problem prior to 2.2). In this scenario (the reason for using the ethtool command) the problem is that tx checksums are not calculated by the virtual interface (because they are being passed in memory rather than on a physical medium) and when pf gets those packets, the checksums obviously don't match and the packets are dropped.

 I think I may have found a lead as to how to resolve the issue, but still have no idea how to implement it. Libvirt provides [hook scripts ]("https://libvirt.org/hooks.html")to include networking. I did some searching to see if I could find how people are using it, but found nothing down at my level yet.

---

### Post by TheFu on 2017-06-11
I'm not using virtio.  Using the e1000 HW emulation.  That would explain why mine just works. The VM was setup years ago - perhaps before virtio was supported by FreeBSD?  IDK.  I don't use virtIO on Windows very often either. Any hassle, is too much at this stage of my career.

My physical pfSense router uses Intel NICs too.

---

### Post by anderbak on 2017-06-11
I just resolved it by dropping in another physical adapter. Luckily, I had a 1-slot GPU cooler that was forcibly compatible with my video card, as my last remaining open slot was being covered by a ridiculous 2-slot cooler. Finally. Now the host can be rebooted and the pfSense guest starts all on it's own and the network just comes up and works as it should. No extra commands have to remembered a month or six down the road.

Looking at your last post, it may have been just as easy to utilize the e1000 device on the VM. Maybe, I gained a smidge of performance with the hardware device since it probably offloads some work from the CPU - no matter, it works now.

Your thoughts are much appreciated. If I ever find an actual solution, I'll follow up in this thread.

---

