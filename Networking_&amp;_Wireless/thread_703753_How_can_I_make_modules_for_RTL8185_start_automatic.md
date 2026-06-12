---
title: "How can I make modules for RTL8185 start automatically"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by fedor.tyurin on 2008-02-21
Hello everyone,

I need your help with Realtek 8185 wireless card.

I've plugged in this card and lshw -C network shows:
  *-network:0 UNCLAIMED            
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: wlan0
       version: 20
       serial: 00:1a:9f:91:b3:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 10
       serial: 00:0c:6e:fd:d6:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.34 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

Ubuntu did not find it automatically.

Then I've download last driver from Realtek web site (modules from Realtek's CD probably were for older kernel - i'm using Ubuntu 7.10 with kernel 2.6.22). I successfully compiled drives and I can use them using insmod. When modules are inserted and wlan0 is up iwconfig returns the following:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.412 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-243 dBm  Noise level=-156 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But I don't know how to make them start automatically.

I've tried to copy modules to /lib/modules/2.6.22.9/kernel/net/wireless/ and  /lib/modules/2.6.22.9/kernel/net/ieee80211/ and add wlan0 to /etc/network/interfaces, but it did not help.

Please help me. The main problem is that I don't understand how to make module "visible" for kernel. 

Any support will be helpful. Thank you!

---

### Post by gdzsi on 2008-02-22
Edit /etc/modules, write the name of the module in it, then it should start.

---

### Post by silver-city-productions on 2008-02-22
You might need to set the essid manually, like 
sudo iwconfig wlan0 essid yrnetworkname

Before finding out if you can connect automatically on startup, make sure you are able to connect to the network at all.  I found that I got in some recovery situations just hanging on startup on the network.  

I am not sure if there has been more work on the kernel supplied r8180 driver, but also be aware that there are reports of it's having various issues.  Myself, I finally got the card working by using the win98 drivers under ndiswrapper on 32-bit linux.

---

### Post by fedor.tyurin on 2008-06-11
> **silver-city-productions said:**
> You might need to set the essid manually, like 
sudo iwconfig wlan0 essid yrnetworkname

Before finding out if you can connect automatically on startup, make sure you are able to connect to the network at all.  I found that I got in some recovery situations just hanging on startup on the network.  

I am not sure if there has been more work on the kernel supplied r8180 driver, but also be aware that there are reports of it's having various issues.  Myself, I finally got the card working by using the win98 drivers under ndiswrapper on 32-bit linux.

In my case driver works fine, i'm writing this using wireless connection :guitar:

Probably newer driver from the web site is better

---

