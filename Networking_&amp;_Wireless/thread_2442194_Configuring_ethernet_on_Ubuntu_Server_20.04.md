---
title: "Configuring ethernet on Ubuntu Server 20.04"
date: 2020-04-30
forum: Networking &amp; Wireless
---

### Post by porkpiehat2 on 2020-04-30
I just installed Ubuntu Server 20.04 on a little Gigabyte Brix mini-PC, and I'm struggling to get a network connection going. Bear in mind, I'm quite new to this but I want to learn!
Originally I planned on setting up wifi as described here: [https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection](https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection)
But that still requires to install packages. I thought I'd take the easy way out and connect directly via Ethernet (will need that in the future anyway). Should be straightforward with a dynamic IP, right?

I've been trying for several hours and cannot get it to work. I followed the steps in the link, without the wifi part. I took the simplest configuration file from the Netplan examples.
The ethernet device is enabled and *should* be working to what I can see. I rebooted each time I modified the file.
In the router I can see it is not connected, and also I cannot ping local devices. Any ideas what I'm missing here?

This is the netplan configuration file (01-netcfg.yaml)
```
# This is the network config written by 'subiquity'network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: true

```

This is the output from the generate:
```
** (generate:1124): DEBUG: 22:39:30.821: Processing input file /etc/netplan/00-installer-config.yaml..
** (generate:1124): DEBUG: 22:39:30.823: starting new processing pass
** (generate:1124): DEBUG: 22:39:30.823: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:1124): DEBUG: 22:39:30.823: starting new processing pass
** (generate:1124): DEBUG: 22:39:30.824: We have some netdefs, pass them through a final round of validation
** (generate:1124): DEBUG: 22:39:30.824: enp3s0: setting default backend to 1
** (generate:1124): DEBUG: 22:39:30.824: Configuration is valid
** (generate:1124): DEBUG: 22:39:30.824: Generating output files..
** (generate:1124): DEBUG: 22:39:30.824: NetworkManager: definition enp3s0 is not for us (backend 1)
(generate:1124): GLib-DEBUG: 22:39:30.824: posix_spawn avoided (fd close requested) 
```

Ethernet device is enabled (output of "lshw -C network"):
```
  *-network DISABLED
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 83
       serial: e4:f8:9c:02:9b:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-26-generic firmware=17.3216344376.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:52 memory:f7100000-f7101fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 40:8d:5c:33:b8:83
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:e000(size=256) memory:f7000000-f7000fff memory:f0000000-f0003fff

```

And finally the output of "ip a":
```
: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 40:8d:5c:33:b8:83 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::428d:5cff:fe33:b883/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e4:f8:9c:02:9b:c1 brd ff:ff:ff:ff:ff:ff
```

---

### Post by The Cog on 2020-04-30
Edit: Deleted first suggestion - it was rubbish.

Or you could try and veriy that it's a DHCP problem (or not) by trying a manual DHCP request:
```
sudo dhclient enp3s0
```

---

### Post by Tadaen_Sylvermane on 2020-04-30
netplan is fairly simple but spacing and such is key. here is how i would write it. single spaces for indention. if you have multiple netplan configs in the directory you may need to disable the ones you don't want. I usually disable all but the one I'm using. but i'm sure there are advanced reasons to keep more than 1.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp3s0:
   dhcp4: true
   dhcp6: false
```

Static ip would be similar

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp3s0:
   dhcp4: false
   dhcp6: false
   addresses: [192.168.1.2/24]
   gateway4: 192.168.1.1
   nameservers:
    addresses: [8.8.8.8]
```

---

### Post by porkpiehat2 on 2020-05-01
> **Tadaen_Sylvermane said:**
> netplan is fairly simple but spacing and such is key. here is how i would write it. single spaces for indention.
That's what I though as well, it looked very simple to me.
I double-checked it. I used double spacing, but the configuration seemed to get through with "generate". Also it responded to the "optional: yes" parameter, so it wouldn't wait for the connection at boot. Changed it to single spacing though, rebooted, but no it made no difference unfortunately.

> [COLOR=#000000]Or you could try and veriy that it's a DHCP problem (or not) by trying a manual DHCP request[/COLOR][COLOR=#000000]
Ran that as well. It takes several minutes to finish, and after that nothing has changed. Ping still returns "Network is unreachable", even a ping to the router. And in the router it does not show up as connected device.

Any other suggestions?[/COLOR]

---

### Post by TheFu on 2020-05-01
Here's mine:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enxc0335eee724f:
      dhcp4: true

```
Then 
```
sudo netplan generate
sudo netplan apply --debug

```

Just change the enx....... for enp3s0.

Tadaen_Sylvermane's file should work too. Note how the first line is "network:"?  I think that could be important.

I see you have the dreaded, RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller rev:0c card.  Ouch. I have one of those on my NFS server. I have the same driver and firmware=rtl8168g-2_0.0.1 that you have too on that machine.  

It started acting flaky, dropping packets, a few years ago, so I dropped in a $10 Marvell 88E8001 GigE card that was laying around here and never worried about it again. The Marvell isn't all that fast, but it was cheap in 2005. Effectively free to me when I needed it. Back then, GigE cards that did 900 Mbps were $200+ and it just wasn't THAT important to me at the time. Think iperf3 only gets about 600 Mbps with it. That's faster than any of my storage, so it doesn't matter.  If I didn't have that NIC laying around, I'd get one of the Intel PRO/1000 or a21[012] series NICs for $25. Intel does network cards so much better than the others. I filter systems/motherboards by whether they have Intel NICs or not. There are reasons that you can look up.

With a NUC, you are stuck. No replacement/upgrade possible. Perhaps use a USB3-to-GigE adapter for $22?  Being small brings problems when swapping a NIC is needed. 

I had one of the early NUC system. When it overheated, it became a brick. Nothing was replaceable. Nothing.  Next time I wanted a smaller system, built an ITX solution. It was smaller than a shoebox, but much more serviceable inside. Often, they have 2 PCIe slots on ITX systems.  That's for the future.

---

### Post by porkpiehat2 on 2020-05-04
Thanks for the elaborate reply, TheFu. Especially the part about the ethernet controller.
I double checked my configuration file, tried yours and Tadaen_Sylvermane's. No luck with either. This got me thinking about your remark. I installed Win 10 on it again, which should connect with ethernet automatically. It sort of connects and I can see the device in the router, but it does not obtain an IP address and hence does not have internet access. Looks like we have suspect...

I'll try to get this working first - or switch to the USB-to-ethernet adapter - and then try Ubuntu Server again. Thanks for the help!

---

### Post by TheFu on 2020-05-04
You can try a few other things.
* use a different CAT5e cable
* use a different switch port

Be certain to check the ifconfig output for dropped/error packets.
If you use NFS, the **nfsstat** command will show the issues clearly too.  Also, be certain to force NFS to use TCP, not UDP. Wouldn't want data corruption over something simple like this when we all have fast networks.

The USB3-to-GigE adapters will get hot and are a stop-gap.  Good enough for desktops, but I wouldn't use one on a server. The drivers are usually some brand we've never heard before. Mine uses the ax88179_178a <--- ever heard of them?  I hadn't.

---

### Post by porkpiehat2 on 2020-05-06
I've tried some more under Windows 10, it won't obtain an IP address. Someone solved it by setting a static IP. Will try that later, and if that works I will switch back to Ubuntu server and set up a static IP there too. That is anyway better for the server.

It's a hard lesson learned, ouch!

---

### Post by coconutdog2 on 2020-07-19
My config that works:

```
---network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
       dhcp4: false
       dhcp6: false
       addresses:
        - 10.1.1.58/24
        - 2001:44b8:xxxx:3b10::58/64
        - fe80::58/64
       gateway4: 10.1.1.1
       gateway6: 2001:44b8:xxxx:3b10::5520
       nameservers:
         addresses:
          - 192.231.203.132
          - 192.231.203.3
          - 2001:44b8:1::1
          - 2001:44b8:2::2
       routes:
         - to: 0.0.0.0/32
           via: 10.1.1.1
           metric: 100
         - to: ::/0
           via 2001:44b8:xxxx:3b10::5520/64
           metric: 100
#
    enp4s0:
       dhcp4: false
       dhcp6: false
       addresses:
        - 10.1.6.58/24
        - 2001:44b8:xxxx:3b60::58/64
        - fe80::58/64
       gateway4: 10.1.6.1
       gateway6: 2001:44b8:xxxx:3b60::5520
       nameservers:
         addresses:
          - 192.231.203.132
          - 192.231.203.3
          - 2001:44b8:1::1
          - 2001:44b8:2::2
       routes:
         - to: 0.0.0.0/32
           via: 10.1.6.1
           metric: 200
         - to: ::/0
           via 2001:44b8:xxxx:3b60::5520/64
           metric: 200
#
    enp4s1:
       dhcp4: false
       dhcp6: false

...
```

The metric command sets the precedence for the default gateways. It will try 10.1.1.1 before it tries 10.1.6.1. My Cisco 5520 is my default gateway. I have an Ubuntu Server 20.04 acting as a DHCP & DHCPv6-PD server. enp4s1 is not currently being used.

---

### Post by shurur9 on 2020-08-19
Just my  2 cents on this.

After installing ubuntu through VPN that was setup by ubuntu in the install process, i disconnected the lan line and connected  through wifi.
I noticed the bootup was waiting to connect to the network through the ethernet line, but would time out and boot up connecting to wifi.
I disabled the internet cable connection because I got sick of waiting for the timeout  (still looking on line/message to figure out what I did..but can't remember the message)
I probably deleted some files....


So today I was trying to get wired internet running:
I was not getting wired settings at all in my network window at all.

hours later...
it dribbled down to the /etc/netplan/[COLOR=#000000]00-installer-config.yaml, that was the name of the file that I found..
I wrestled with the syntax for quite a while...along with repeated 
>sudo netplan apply
> sudo service network-manager restart

**What made it all work was my commenting out every line in the .yaml file.**

I don't know why it works.
Maybe it causes some address discovery to happen? arp

I have got my wired network window now.[/COLOR]

---

### Post by coconutdog2 on 2020-08-20
I'd say you have some dodgy stuff going on in your .yaml file. It is very particular as to how you indent the lines. There is no hard and fast rule, you do have to be consistent though. Also, never use tabs. If you want your renderer to be netplan, use this:

```
[COLOR=#000000][FONT=&quot]renderer: networkd[/FONT][/COLOR]
```

As I have shown. If you want networkManager to be the renderer use:

```
renderer: NetworkManager
```

One or the other. I also find the following to be more informative:

```
netplan --debug try
```

and

```
netplan --debug apply
```

I prefer networkd as this is the way Ubuntu is going. It is the default on Ubuntu Server 20.04. I also prefer to use the CLI than the NetworkManager GUI.

Good luck, keep trying.

---

### Post by shurur9 on 2020-08-20
Yes, 

Ok Tabs are bad..good to know.

When someone gets this down as to what information needs to be extracted and properly put into the .yaml file so it will "compile"  with proper syntax, then make a script.."we" will really have something.

Something that runs terminal commands, dumps to a file, then searches the file and creates the .yaml file.

A simple one for DT guys...and a panzer tank one for systems guys with bridges and such.

I was a network HW designer; though you wouldn't know it...I don't speak the language anymore..sorry.

---

### Post by TheFu on 2020-08-20
Sure the router/dhpc server isn't the problem?

---

