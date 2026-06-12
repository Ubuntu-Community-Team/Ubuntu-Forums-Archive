---
title: "Problem with Realtek RTL8723AE - poor wifi signal, suddenly freezes"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by witold.szklarski on 2014-01-02
Hi

I have a problem with my laptop Toshiba Satellite C855-2CQ. I installed Ubuntu 13.10 over Windows 8 but have some problems with Wifi. Signal strength is very poor but wifi icon with range trate from minumum range to max and connection drops frequently. I'm using laptop in other room about 6 to 8 metres from router and had no problem with signal using windows.

Here's my outputs:

```
witold@witold-SATELLITE-C855-2CQ:~$ ip addr1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 7c:05:07:09:5c:c5 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 2c:d0:5a:65:39:49 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.15/24 brd 192.168.0.255 scope global wlan0
       valid_lft forever preferred_lft forever
    inet6 fe80::2ed0:5aff:fe65:3949/64 scope link 
       valid_lft forever preferred_lft forever

witold@witold-SATELLITE-C855-2CQ:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"UPC0050959"  
          Mode:Managed  Frequenc y:2.437 GHz  Access Point: FC:94:E3:03:0B:FD   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0



```

Here's lspci output below:
```
witold@witold-SATELLITE-C855-2CQ:~$ lspci -nnk | grep -iA2 net02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
	Kernel driver in use: rtl8723ae
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fb37]
	Kernel driver in use: r8169



```

I noticed that my wireless card is supported by Ubuntu, but offers poor performance [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI) so
is installing the windows drivers usung ndiswrapper the best solution?

Thank you in advance for any help.

---

### Post by varunendra on 2014-01-04
> **witold.szklarski said:**
> I noticed that my wireless card is supported by Ubuntu, but offers poor performance [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI) so
is installing the windows drivers usung ndiswrapper the best solution?

Welcome to the forums witold.szklarski !

I'm posting here with much hesitation since the person who added the feedback about rtl8723ae card/driver on above wiki page was being helped by myself (in [this thread]("http://ubuntuforums.org/showthread.php?t=2194870")), and obviously we failed to get a decent performance with it.

Since this card seems to have worked decently in the past *(because we didn't have had many problem threads regarding it, and whichever we had, got fixed with some tested solutions that don't work anymore on newer kernels)*, I believe an older kernel/drive may make it work while new updates fix the bugs (if any) again. But using an unsupported version/kernel is not much of a solution just to make wifi work, if at all.

May I suggest to try this post : [http://ubuntuforums.org/showthread.php?t=2194870&p=12883518#post12883518](http://ubuntuforums.org/showthread.php?t=2194870&p=12883518#post12883518) with driver package "3.12-1" instead of the latest as suggested in the post : [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2)

Please have a read of the entire thread I linked above, try the temporary solutions first, then the backported driver suggested above. Let us know how it goes for you.

**PS:**
By the way, I don't think ndiswrapper can offer any better performance than the native driver. But if it is a fresh install, you may try that later if our regular exercises fails to make it stable and fast.

---

### Post by Bucky Ball on 2014-01-04
Welcome. Yes, good advice from varunendra. Avoid ndiswrapper if possible. Largely superseded and consider a last resort.

---

