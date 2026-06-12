---
title: "I run sudo apt-get purge network-manager to fix network problems and it was worst"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by marga2 on 2015-06-08
Hi, I have been having problems with network connections after upgrade to Ubuntu 14.04, I solved before changing the etc/network/interfaces file. With the last updates, the network wasn't working again, it was connected but it wasn't able to browse any page. I tried several things changing the interfaces file again but it doesn't work  and finally following another thread that seemed to have the same problem I run sudo apt-get purge network-manager and now I don't know what to do, network icon is missing and ping to the router and to any page fails.
Thanks in advance

---

### Post by The Cog on 2015-06-08
If you're using static network configuration in /etc/network/interfaces then you don't need network manager.

You may be able to reinstall network manager without a network connection - it may be in the cache.

But anyway, let's concentrate on getting it working with /etc/network/interfaces.
Can you post your existing /etc/network/interfaces contents, and the output from the commands
```
ifconfig
route -n
ping -c3 91.189.94.12
ping -c3 ubuntuforums.org
```
This should give an idea what's happening.

---

### Post by marga2 on 2015-06-08
Hi the Cog, the etc/network/interfaces said the following

```
 auto lo
iface lo inet loopback
```

```
ifconfig
lo  link encamp: Local loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0 
inet6 addr: ::1/128 Scope: Host 
UP LOOPBACK RUNNING   MTU:65536 Metric:1
RX packets:17521 errors:0 dropped:0 overruns:0 frame:0
TX packets:17521 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5433714 (5.4 MB) TX bytes:5433714 (5.4 MB)
```

```
route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
```

```
[COLOR=#000000][FONT=Ubuntu Mono]ping -c3 91.189.94.12
[/FONT][/COLOR]connect:Network is unreachable
```

```
[COLOR=#000000][FONT=Ubuntu Mono]ping -c3 ubuntuforums.org
[/FONT][/COLOR]ping: unknown host ubuntuforums.org
```

Thanks!

---

### Post by Bashing-om on 2015-06-08
marga2; Hello:

Allow me, as it appears The Cog is otherwise pre-occupied, to offer aid:

We can see that /etc/network/interfaces is not configured for any external connection.
BUT, let's do make sure that Network-manager is not a factor here.
What returns:
```

cat /etc/NetworkManager/NetworkManager.conf
cat /etc/dhcp/dhclient.conf

```

Depending on your wishes and requirements, might consider controlling the wired network from  /etc/network/interfaces .

[INDENT][INDENT]in my little mind\
[INDENT][INDENT][INDENT]simpler is better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by The Cog on 2015-06-08
That doesn't look good. You don't appear to actually have a network interface. Maybe it hasn't been brought up by the driver, or maybe the hardware just hasn't been recognised at all.
I don't really know what to do from here, but posting the output of these commands might help people figure out what's wrong:
```
ifconfig -a
ip link
lspvi -v
```

---

### Post by marga2 on 2015-06-08
Hi Bashing-om, the NetworkManager.conf file says the following:
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmask

[ifupdown]
managed=false

```

and dhclient.conf
```

[FONT=Times]# Configuration file for /sbin/dhclient, which is included in Debian's[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    dhcp3-client package.[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]# This is a sample configuration file for dhclient. See dhclient.conf's[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    man page for more information about the syntax of this file[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    and a more comprehensive list of the parameters understood by[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    dhclient.[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]# Normally, if the DHCP server provides reasonable information and does[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    not leave anything out (like the domain name, for example), then[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#    few changes must be made to this file, if any.[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#send host-name "andare.fugue.com";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]send host-name = gethostname();[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#send dhcp-lease-time 3600;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#supersede domain-name "fugue.com home.vix.com";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#prepend domain-name-servers 127.0.0.1;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]request subnet-mask, broadcast-address, time-offset, routers,[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]    domain-name, domain-name-servers, domain-search, host-name,[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]    dhcp6.name-servers, dhcp6.domain-search,[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]    netbios-name-servers, netbios-scope, interface-mtu,[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]    rfc3442-classless-static-routes, ntp-servers,[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]    dhcp6.fqdn, dhcp6.sntp-servers;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#require subnet-mask, domain-name-servers;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#timeout 60;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#retry 60;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#reboot 10;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#select-timeout 5;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#initial-interval 2;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#script "/etc/dhcp3/dhclient-script";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#media "-link0 -link1 -link2", "link0 link1";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#reject 192.33.137.209;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#alias {[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  interface "eth0";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  fixed-address 192.5.5.213;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option subnet-mask 255.255.255.255;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#}[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#lease {[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  interface "eth0";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  fixed-address 192.33.137.200;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  medium "link0 link1";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option host-name "andare.swiftmedia.com";[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option subnet-mask 255.255.255.0;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option broadcast-address 192.33.137.255;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option routers 192.33.137.250;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  option domain-name-servers 127.0.0.1;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  renew 2 2000/1/12 00:00:01;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  rebind 2 2000/1/12 00:00:01;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#  expire 2 2000/1/12 00:00:01;[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#}[/FONT]




```

Thanks again!

---

### Post by marga2 on 2015-06-08
Hi, the Cog, these are the outputs:
```

i[FONT=Times]fconfig -a
[/FONT][FONT=Times]eth0      Link encap:Ethernet  HWaddr 3c:97:0e:5b:13:a8  [/FONT]
[FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Times]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
[FONT=Times]          Interrupt:20 Memory:f2500000-f2520000 [/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]lo        Link encap:Local Loopback  [/FONT]
[FONT=Times]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=Times]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=Times]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=Times]          RX packets:2849 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:2849 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:0 [/FONT]
[FONT=Times]          RX bytes:898646 (898.6 KB)  TX bytes:898646 (898.6 KB)[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]wlan0     Link encap:Ethernet  HWaddr 84:3a:4b:06:55:50  [/FONT]
[FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Times]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]



```

```

[FONT=Times]ip link[/FONT]
[FONT=Times]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default [/FONT]
[FONT=Times]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=Times]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=Times]    link/ether 3c:97:0e:5b:13:a8 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=Times]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=Times]    link/ether 84:3a:4b:06:55:50 brd ff:ff:ff:ff:ff:ff  [/FONT]
[FONT=Times]
[/FONT]

```

```

[FONT=Times]lspvi -v[/FONT]
[FONT=Times]No command 'lspvi' found, did you mean:                                                                                                                                                [/FONT]
[FONT=Times] Command 'lspci' from package 'pciutils' (main)                                                                                                                                        [/FONT]
[FONT=Times]lspvi: command not found    [/FONT]



```


Thanks!

---

### Post by Bashing-om on 2015-06-08
marga2; Hey;

Looks to me like if you edited /etc/network/interfaces to 'include' this:
```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
and reboot;
You should have a working wired connection.

Else; we look and find the reason why not.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by The Cog on 2015-06-08
^^^ what Bashing-om said. 
The interface is there, but not being brought up.
Add those 3 lines to the end of /etc/network/interfaces and then reboot.
If that doesn't fix it then try those 3 commands from #5 again.

---

### Post by marga2 on 2015-06-08
Adding the three lines to the interfaces file doesn't work, not with wired connection, not with wireless. 
The new interfaces file:
```

[FONT=Times]auto lo[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]iface lo inet loopack

[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]#the primary network interface[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]auto eth0[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]iface eth0 inet dhcp[/FONT]

```


And the outputs from #5 are:
```

[FONT=Times]ifconfig -a[/FONT]
[FONT=Times]eth0      Link encap:Ethernet  HWaddr 3c:97:0e:5b:13:a8  [/FONT]
[FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Times]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
[FONT=Times]          Interrupt:20 Memory:f2500000-f2520000 [/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]lo        Link encap:Local Loopback  [/FONT]
[FONT=Times]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=Times]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=Times]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=Times]          RX packets:237 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:0 [/FONT]
[FONT=Times]          RX bytes:89466 (89.4 KB)  TX bytes:89466 (89.4 KB)[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]wlan0     Link encap:Ethernet  HWaddr 84:3a:4b:06:55:50  [/FONT]
[FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Times]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Times]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/FONT]
```
[FONT=Times]
[/FONT]```

[FONT=Times] ip link[/FONT]
[FONT=Times]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default [/FONT]
[FONT=Times]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=Times]2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=Times]    link/ether 3c:97:0e:5b:13:a8 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=Times]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000[/FONT]
[FONT=Times]    link/ether 84:3a:4b:06:55:50 brd ff:ff:ff:ff:ff:ff[/FONT]

```[FONT=Times]

[/FONT]```
[FONT=Times]
 lspvi -v
[/FONT][FONT=Times] No command 'lspvi' found, did you mean:[/FONT]
[FONT=Times] Command 'lspci' from package 'pciutils' (main)[/FONT]
[FONT=Times]lspvi: command not found[/FONT]

```[FONT=Times]
[/FONT]


Thanks!

---

### Post by sandyd on 2015-06-08
Try
```

sudo dhclient eth0
```

Wait a while, and see if there is any output

---

### Post by Bashing-om on 2015-06-08
marga2; Humm , 

Surprised that you are not up. Working to get the wired connection .
What results:
```

ifconfig eth0 up

```
and The Cog had a slip of the fingers:
 lsp[color=red]v[/color]i -v should be lspci -v
We still want to see the output of the 'lspci' command.

[INDENT][INDENT]and a hunt'n we will go
[/INDENT][/INDENT]

---

### Post by chili555 on 2015-06-08
I believe, for interfaces declared in /etc/network/interfaces, the command is:```
sudo ifup -v eth0
```-v for verbose should produce some helpful diagnostics.

Poor marga2 has plenty of cooks stirring the broth!!

---

### Post by marga2 on 2015-06-08
Hi Sandyd,

No answer in 2 minutes, I finished it with ctrl+Z.

Thanks

---

### Post by Bashing-om on 2015-06-08
@chili555;

> 
plenty of cooks stirring the broth!!


However, if the last cook stops the broth from burning ->

[INDENT][INDENT]Oh what a good thing
[/INDENT][/INDENT]

---

### Post by marga2 on 2015-06-08
Hi Bashing-om, I run what you suggested using sudo, but it doesn't work, I'm going to restart to see what happen. In the meanwhile, this is the output:
```

[FONT=Times]lspci -v[/FONT]
[FONT=Times]00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0[/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0, IRQ 44[/FONT]
[FONT=Times]        Memory at f0000000 (64-bit, non-prefetchable) [size=4M][/FONT]
[FONT=Times]        Memory at e0000000 (64-bit, prefetchable) [size=256M][/FONT]
[FONT=Times]        I/O ports at 5000 [size=64][/FONT]
[FONT=Times]        Expansion ROM at <unassigned> [disabled][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: i915[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, medium devsel, latency 0, IRQ 40[/FONT]
[FONT=Times]        Memory at f2520000 (64-bit, non-prefetchable) [size=64K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: xhci_hcd[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0, IRQ 43[/FONT]
[FONT=Times]        Memory at f2535000 (64-bit, non-prefetchable) [size=16][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: mei_me[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])                                                                     [/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa                                                                                                                                                            [/FONT]
[FONT=Times]        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19                                                                                                                                 [/FONT]
[FONT=Times]        I/O ports at 50b0 [size=8]                                                                                                                                                               [/FONT]
[FONT=Times]        Memory at f253c000 (32-bit, non-prefetchable) [size=4K]                                                                                                                                  [/FONT]
[FONT=Times]        Capabilities: <access denied>                                                                                                                                                            [/FONT]
[FONT=Times]        Kernel driver in use: serial                                                                                                                                                             [/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21f3[/FONT]
[FONT=Times]        Flags: fast devsel, IRQ 20[/FONT]
[FONT=Times]        Memory at f2500000 (32-bit, non-prefetchable) [disabled] [size=128K][/FONT]
[FONT=Times]        Memory at f253b000 (32-bit, non-prefetchable) [disabled] [size=4K][/FONT]
[FONT=Times]        I/O ports at 5080 [disabled] [size=32][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: e1000e[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, medium devsel, latency 0, IRQ 16[/FONT]
[FONT=Times]        Memory at f253a000 (32-bit, non-prefetchable) [size=1K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: ehci-pci[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0, IRQ 45[/FONT]
[FONT=Times]        Memory at f2530000 (64-bit, non-prefetchable) [size=16K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: snd_hda_intel[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0[/FONT]
[FONT=Times]        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0[/FONT]
[FONT=Times]        I/O behind bridge: 00004000-00004fff[/FONT]
[FONT=Times]        Memory behind bridge: f1d00000-f24fffff[/FONT]
[FONT=Times]        Prefetchable memory behind bridge: 00000000f0400000-00000000f0bfffff[/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: pcieport[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0[/FONT]
[FONT=Times]        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0[/FONT]
[FONT=Times]        Memory behind bridge: f1c00000-f1cfffff[/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: pcieport[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0[/FONT]
[FONT=Times]        Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0[/FONT]
[FONT=Times]        I/O behind bridge: 00003000-00003fff[/FONT]
[FONT=Times]        Memory behind bridge: f1400000-f1bfffff[/FONT]
[FONT=Times]        Prefetchable memory behind bridge: 00000000f0c00000-00000000f13fffff[/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: pcieport[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, medium devsel, latency 0, IRQ 23[/FONT]
[FONT=Times]        Memory at f2539000 (32-bit, non-prefetchable) [size=1K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: ehci-pci[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, medium devsel, latency 0[/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: lpc_ich[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41[/FONT]
[FONT=Times]        I/O ports at 50a8 [size=8][/FONT]
[FONT=Times]        I/O ports at 50bc [size=4][/FONT]
[FONT=Times]        I/O ports at 50a0 [size=8][/FONT]
[FONT=Times]        I/O ports at 50b8 [size=4][/FONT]
[FONT=Times]        I/O ports at 5060 [size=32][/FONT]
[FONT=Times]        Memory at f2538000 (32-bit, non-prefetchable) [size=2K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: ahci[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: medium devsel, IRQ 11[/FONT]
[FONT=Times]        Memory at f2534000 (64-bit, non-prefetchable) [size=256][/FONT]
[FONT=Times]        I/O ports at efa0 [size=32][/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07) (prog-if 01)[/FONT]
[FONT=Times]        Subsystem: Lenovo Device 21fa[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0, IRQ 16[/FONT]
[FONT=Times]        Memory at f1d00000 (32-bit, non-prefetchable) [size=256][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: sdhci-pci[/FONT]
[FONT=Times]
[/FONT]
[FONT=Times]03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)[/FONT]
[FONT=Times]        Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN[/FONT]
[FONT=Times]        Flags: bus master, fast devsel, latency 0, IRQ 46[/FONT]
[FONT=Times]        Memory at f1c00000 (64-bit, non-prefetchable) [size=8K][/FONT]
[FONT=Times]        Capabilities: <access denied>[/FONT]
[FONT=Times]        Kernel driver in use: iwlwifi[/FONT]


```

Thanks!!!!

---

### Post by marga2 on 2015-06-08
Hi Chili555, I really appreciate your interest. This is the output for your suggestion:
```

[FONT=Times]sudo ifup -v eth0[/FONT]
[FONT=Times]/etc/network/interfaces:2: unknown method[/FONT]
[FONT=Times]ifup: couldn't read interfaces file "/etc/network/interfaces"[/FONT]

``` 

Thanks a lot to all of you for your help!!!

---

### Post by marga2 on 2015-06-08
I reboot and nothing :(, I have a flight tomorrow, I'm going to sleep. I will be trying again tomorrow evening!!!
Thanks!!

---

### Post by chili555 on 2015-06-08
> /etc/network/interfaces:2: unknown methodThat means there is an error somewhere in the file. Let's have a look and we'll fine-tune it:```
cat /etc/network/interfaces
```

---

### Post by marga2 on 2015-06-09
Chili555 in #10 I modified the interfaces file, the first piece  of code there corresponds to that file. 
Thanks

---

### Post by marga2 on 2015-06-09
Chili555 in #10 I modified the interfaces file, the first piece  of code there corresponds to that file. 
Thanks

---

### Post by chili555 on 2015-06-09
So your file is exactly this; no more and no less?```
auto lo
iface lo inet loopack

#the primary network interface
auto eth0
iface eth0 inet dhcp
```I think *ifup* is complaining because you misspelled loopback. Please correct it and try again:```
sudo ifdown eth0 && sudo ifup -v eth0
```

---

### Post by The Cog on 2015-06-09
I meant to type ```
lspci -v
```Sorry about that error. It should list the PCI bus and tell us what tyope of network card you have, along with the driver in use for it.

It is possible that the spelling error that chili555 spotted is causing problems. I suggest fix that first, reboot, and then run the above command if it still doesn't work.

---

### Post by marga2 on 2015-06-10
Hi all,
now I only have the possibility of wireless connection, I corrected the typo in interfaces file and I found how to connect to wifi using the terminal, and I did it :p. Now I don't know how to re install the network manager but I think that could be in other thread...thanks to all for the help!

---

### Post by chili555 on 2015-06-10
> **marga2 said:**
> Hi all,
now I only have the possibility of wireless connection, I corrected the typo in interfaces file and I found how to connect to wifi using the terminal, and I did it :p. Now I don't know how to re install the network manager but I think that could be in other thread...thanks to all for the help!If this is a stay at home computer that always connects to the same network, you don't really need NM; leave it as it is.

If you need to take the computer to the coffee shop, library, university, etc., then, with a working internet connection:```
sudo apt-get install network-manager
```Several prerequisites will also install, reboot and enjoy.

---

