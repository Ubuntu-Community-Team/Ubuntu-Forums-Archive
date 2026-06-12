---
title: "[SOLVED] problematic connection at work"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by tamoneya on 2008-06-13
I am having trouble viewing larger webpages while at work.  Often when using firefox or opera in ubuntu it will get stuck after downloading about 4.3kb of the web page.  This makes it very difficult to get any work done as you can imagine.  I have tried using the internet at work using xp since I have a dual boot and it worked fine(no problems with my network jack or blocked MAC address).  I also have no problem with the internet at home(my ethernet jack is detected and working in linux).  I have tried a couple things like spoofing my user agent thinking that there might be some firewall that is blocking linux but it had no effect.  I asked my boss about this and he said that there isnt any firewall in the network that would be doing that.  Since it is a small company I have actually looked in the routers and such myself and I see nothing to that effect as well.  Here is some information on my hardware and connection:
```
tamoneya@tamoneyat61:~/.FAH$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:3a:ca:4a  
          inet addr:10.100.34.137  Bcast:10.100.34.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fe3a:ca4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2099145 (2.0 MB)  TX bytes:1560460 (1.4 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

```
```
tamoneya@tamoneyat61:~/.FAH$ sudo lshw -C network
[sudo] password for tamoneya: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:3a:ca:4a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=10.100.34.137 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965

```

---

### Post by tamoneya on 2008-06-13
Not sure if it helps but I know that I am getting a userful amount of bandwidth since I am making this post from within linux.  But I have had to make a ssh connection to my server at home and use X11 forwarding to forward firefox to my laptop.  This is in no means idea but it works so it seems to not be a bandwidth issue but more of a per application throttling issue.

---

### Post by tamoneya on 2008-06-13
Problem actually had to do with my router and a imcompatability with my kernel.  At work we use a RV016 and there is a problem with it: [https://help.ubuntu.com/community/WifiDocs/RouterIssues](https://help.ubuntu.com/community/WifiDocs/RouterIssues).

I found my solution here:[http://www.drewb.com/blog/post/view/p/12/title/linksys_rv016_router__firewall__vpn__linux](http://www.drewb.com/blog/post/view/p/12/title/linksys_rv016_router__firewall__vpn__linux)

Thanks

---

