---
title: "D-Link N300 router"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by sbcwinn on 2013-12-02
I used to run Windoze until only a month or two ago. Suddenly my computer stopped communicating with my D-Link N300 router.There are 5 computers in the household, mine was the only one with the problem. After spending many hours with D-Link on the phone I got fed up and I always wanted to delve into Ubuntu, so I did. My wifi issue went away. After another month or so it came back!

The system connects to the router just fine. If I go to the network information its all there. If I try to surf the web, I cannot. If I try to co9ntact the router through the browser it won't find it. If I go to the router, the computer is not listed as a wireless device, although the router's information is howing in the connection information....

Now here is the MOST perplexing part........ If I run Ubuntu from a USB stick, everything works just fine!

HELP PLEASE! This is drving me nuts.

I am running UBUNTU 13.10 on an Acer E1-532 laptop (very new.....) computer.

---

### Post by Bucky Ball on 2013-12-02
Did an update break it or did you install something and it stopped working? Did it just stop worked randomly with no apparent cause?

Perhaps give us the output of these two commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by sbcwinn on 2013-12-02
It totally stopped randomly. I had the same problem in Windoze.

PS - I love Ubuntu and want to stay here!

---

### Post by Bucky Ball on 2013-12-02
So it doesn't work in Windows either? Could you provide the output of the two commands in my last thread from a terminal, thanks. ;)

---

### Post by sbcwinn on 2013-12-03
I haven't had a chance to run your 2 commands but just to add to the perplexity .....

The computer works perfectly with any other router but any D-Link 615 N300 router. I have 4 other computers at home that work with this router just fine.....

---

### Post by sbcwinn on 2013-12-03
Here is the output from the commands that you suggested....

   *-network                
        description: Ethernet interface  
        product: NetLink BCM57785 Gigabit Ethernet PCIe  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 10  
        serial: 20:89:84:6f:26:e5  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=sb latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff  
   *-network  
        description: Wireless interface  
        product: BCM4313 802.11bgn Wireless Network Adapter  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth1  
        version: 01  
        serial: 1c:3e:84:6b:a4:3c  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11abg  
        resources: irq:17 memory:c0500000-c0503fff  
 

 

 eth0      no wireless extensions.  
 

 eth1      IEEE 802.11abg  ESSID:"dlink"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: C8:D3:A3:57:D7:EA    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
            
 lo        no wireless extensions.

---

### Post by sbcwinn on 2013-12-04
I do not know why the copy/paste put in emoticons. Sorry about that!

---

