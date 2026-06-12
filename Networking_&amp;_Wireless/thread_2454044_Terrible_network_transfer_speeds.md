---
title: "Terrible network transfer speeds"
date: 2020-11-22
forum: Networking &amp; Wireless
---

### Post by blackmyre on 2020-11-22
I'm getting extremely poor network transfer rates from a new (and updated) install of Ubuntu Server20.04 LTS in a new Virtual Machine. Other machines on the LAN, including existing VMs on the same physical host as the Ubuntu VM, have transfer rates that are orders of magnitude faster so presumably it's not a hardware or cabling issue. Running ethtool confirms that Ubuntu is seeing a gigabit NIC. 

At first I thought it might be a CIFS issue but I've now tried NFS with much the same results: about 30 **Kilobytes**/s from the Ubuntu Server. Other machines on the wired LAN (physical and VM) are getting about 25-50 **Megabytes**/s, and even my laptop with slow WiFi is getting in the megabyte range.

The other setups I've tried are: Mint 18.3; OpenMediaVault [Debian stretch-based]; Mint 20.0. All manage megabyte speeds compared with ~30KB/s in Ubuntu Server 20.04.

I found some posts about transfer speed issues but they turned out to be related to WiFi settings/drivers but I'm using wired connections (virtual NICs through the host's physical card). I don't have enough experience to know where else to look for the cause of the problem. Can anyone point me in the right direction and/or tell me what other information I need to post to help narrow it down?

Thanks for any assistance.

---

### Post by TheFu on 2020-11-22
Let's start by saying clearly, exactly, which hypervisor you are using.
Is this a bridge connection or something else? How is that setup?

I'm using KVM with virtio drivers for a 20.04 desktop and seeing no issues. The bridge is manually setup using the interfaces file.  The VM networking is static using a netplan config file.  From the VM to the host, I see 20-30 Gbps.  To other systems with GigE NICs, usually 920-940 Mbps.  On of my systems has a terrible Realtek NIC, where I see 550Mbps, but with Intel NICs, the performance is almost always good or great.

When talking network performance, bits/sec is commonly used and all network hardware is rated using those units, not bytes.

---

### Post by Doug S on 2020-11-23
> **TheFu said:**
> Let's start by saying clearly, exactly, which hypervisor you are using.
Is this a bridge connection or something else? How is that setup?Yes, agree.

> **TheFu said:**
> I'm using KVM with virtio drivers for a 20.04 desktop and seeing no issues. The bridge is manually setup using the interfaces file.  The VM networking is static using a netplan config file.As much for my own interest, as contributing to this thread, I did the same tests: Host = Debian server; bridge manually setup using networkd (I do not use netplan); VM IP address is dynamic via my main test network dhcp server on the same host computer; QEMU/KVM with virtio drivers; Guest = Ubuntu desktop 20.10.

> **TheFu said:**
>   From the VM to the host, I see 20-30 Gbps. I did a 300 second test using iperf:

```
doug@desk-gg:~$ iperf -c s15 -t 300 --window 416K
------------------------------------------------------------
Client connecting to s15, TCP port 5001
TCP window size:  416 KByte
------------------------------------------------------------
[  3] local 192.168.111.4 port 41342 connected with 192.168.111.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-300.0 sec   700 GBytes  [COLOR="#FF0000"]20.0 Gbits/sec[/COLOR]
```



> **TheFu said:**
>  To other systems with GigE NICs, usually 920-940 Mbps. I did a 300 second test using iperf:

```
doug@desk-gg:~$ iperf -c s18 -t 300 --window 416K
------------------------------------------------------------
Client connecting to s18, TCP port 5001
TCP window size:  416 KByte
------------------------------------------------------------
[  3] local 192.168.111.4 port 40382 connected with 192.168.111.122 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-300.0 sec  29.1 GBytes   [COLOR="#FF0000"]835 Mbits/sec[/COLOR]
```Note the VM guest takes a lot more energy to do the same thing compared to doing it from the host. I am saying that the host processor consumes 33 watts while running the iperf command to a different piece of hardware, whereas the host doing the same (the VM is still active, but idle) thing uses only 7.1 watts (similar performance result, 830 Mbits/sec).

---

