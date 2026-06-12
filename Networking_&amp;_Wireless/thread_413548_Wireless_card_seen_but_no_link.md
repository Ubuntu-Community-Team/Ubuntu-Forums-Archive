---
title: "Wireless card seen but no link"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by table32 on 2007-04-19
Hi,

I've installed xubuntu 6.10 on an ageing HP OmniBook 900B, 128Mb ram, 12 gb disk. So far so good, it's breathed life back into the old beast, and as a Linux newbie, I'm impressed how easy it was.

But, no joy with the wireless network card - a noname  PC card with a realtek 8180L chipset. 

When I run Network Settings, I can see the card, and enable it. The TX/RX light flashes, but the link light never comes on. I have tried using DHCP and a static IP address, neither works. There is no WEP security, the wireless router is open to allcomers.

Here's all the diagnostic output I could gather, hopefully this is something really simple I'm overlooking!

Running iwconfig gives the following output:

> 
lo        no wireless extensions.

wlan0     802.11b  ESSID:"moulin"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Running ifconfig gives this:

> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1744 (1.7 KiB)  TX bytes:1744 (1.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:0A:65:BB  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10486 (10.2 KiB)
          Interrupt:10 Memory:c8942000-c8942100 


The command sudo lshw -C network reports the following:

> 
  *-network               
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0e:2e:0a:65:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b
       resources: ioport:1000-10ff iomemory:12000000-120001ff irq:10


sudo iwlist wlan0 scan returns this:

> wlan0     No scan results

(The machine is right next to the wireless router, and other machines in the room are connected no problem)

If I try and PING the router, with a static IP address set in Network Settings, I  get this:

> 
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.5 icmp_seq=1 Destination Host Unreachable
From 192.168.0.5 icmp_seq=2 Destination Host Unreachable
From 192.168.0.5 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3007ms
, pipe 3


If I change to DHCP, and then ping the router, perhaps unsurprisingly it changes to this result:

> 
ping 192.168.0.1
connect: Network is unreachable


I'd love to make this work, otherwise the old machine will end up back in the cupboard! Am I missing something obvious? I've read about ndiswrapper on this forum, but haven't tried it as is looks like the native driver is loaded.

The pc card does work in the same machine under XP, so I can count that out as the problem.

In hope....

Henry

---

### Post by woro2006 on 2007-04-19
[follow this post]("http://ubuntuforums.org/showthread.php?t=389686&highlight=f5d7000")

[Download the drivers here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L")

The process is similar to the post above, except if you have an existing driver, you have to remove it. 
List all available drivers
ndiswrapper -l 
remove it by
ndiswrapper -r [drivername]

---

### Post by table32 on 2007-04-19
Well that's odd - I got as far as installing ndiswrapper and it just started working! Never even got to the downloading the windows driver part! 

Thanks for your help!!

---

