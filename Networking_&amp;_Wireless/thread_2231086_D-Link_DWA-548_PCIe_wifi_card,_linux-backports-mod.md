---
title: "D-Link DWA-548 PCIe wifi card, linux-backports-modules for Trusty Tahr, Bonding"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by Steve_Par on 2014-06-23
Hi,
 

 Okay, here's the background.  I have a desktop computer running Ubuntu 14.04 Trusty Tahr.  It has an on-board ethernet connection with which I connect to my switch using a rather slow (about 10 Mbps) powerline LAN.  As I recently installed fibre in my home I can now consistently obtain a faster connection to the internet, but the bottleneck on my LAN is the powerline interface.  Also, 10 Mbps isn't that fast when I'm transferring data internally from one device to another on my LAN.  So, I thought the easiest solution would be to install a wifi card in my desktop and then bond the ethernet and wlan ports to increase the available bandwidth.
 

 I now have a D-Link DWA-548 PCIe wifi card installed on my desktop (thanks to chili555 for his help in talking me through the driver installation!).  I notice, however, that the driver is not loading upon boot and therefore in my Network Connections Manager upon booting only the Enable Networking line shows as ticked and the Enable Wi-Fi doesn't show at all either ticked or unticked.
 

 nmcli nm shows:-
 

 ```

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled


``` 

 iwconfig shows:-
 

 ```
eth0      no wireless extensions. 

  
 lo        no wireless extensions.

``` 

 sudo lshw -C network shows:-
 

 ```
*-network                

        description: Ethernet interface 
        product: NetXtreme BCM5764M Gigabit Ethernet PCIe 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 10 
        serial: d0:27:88:07:63:94 
        size: 100Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5764m-v3.35 ip=192.168.100.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:45 memory:feaf0000-feafffff 
   *-network UNCLAIMED 
        description: Network controller 
        product: RT5392 PCIe Wireless Network Adapter 
        vendor: Ralink corp. 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        version: 00 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: memory:febf0000-febfffff 

``` 

Although I note that after I run 

```
sudo modprobe rt2800pci
```

sudo lshw -C network becomes:-

```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: d0:27:88:07:63:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5764m-v3.35 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:feaf0000-feafffff
  *-network
       description: Wireless interface
       product: RT5392 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: c4:a8:1d:03:66:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-29-generic firmware=0.34 ip=192.168.100.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff

```

nmcli nm remains unchanged:-

```

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
```

And iwconfig shows:-
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ICRFibre"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 76:7B:E8:D4:4A:67   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:197   Missed beacon:0

```


 My research seems to suggest that in order to get the RT5392 PCIe Wireless Network Adapter to work properly I need to 

```
sudo apt-get install linux-backports-modules-trusty
```

 although it seems as though no backport modules are yet available for 14.04 trusty.
 

 I'm also a little confused about whether I need ndiswrapper at all given that I appear to be using a Linux native Wireless Driver rt2800pci, so I am unclear why I should need ndiswrapper installed at all.
 

 Finally, when I tried to follow [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) I note that
 
```
sudo stop networking
```

 didn't work.
 

 Any insights, ideas or suggestions that anyone can offer would be gratefully received.
 

 Thanks,

---

### Post by chili555 on 2014-06-23
First, let's deal with the modprobe rt2800pci issue. I suspect that Network Manager sees that the ethernet is connected; i.e. detects a carrier signal, and concludes that you don't really need the wireless today. The driver doesn't load, the interface doesn't start, etc. If you detach the ethernet and reboot, is the result the same? If so, it's easy to fix.

If you reboot without the ethernet and the wireless starts as expected, does it pass traffic both within your home network and the internet?

Why do you think you need bonding? I'm not arguing that you don't (yet), I just want to better understand your network and situation.>  it seems as though no backport modules are yet available for 14.04 trusty.Correct. I wouldn't install any backports package or ndiswrapper unless I found rt2800pci lacking. Have you, aside from the perhaps expected refusal to load on boot which is easily fixable?

---

### Post by Steve_Par on 2014-06-23
Hi Chili,

Yes, I disconnected the ethernet cable and booted and nothing happened, i.e. the wifi didn't connect and the RT5392 PCIe Wireless Network Adapter remained UNCLAIMED.

The reason I'm thinking of bonding the wlan port and the ethernet port is simply an exercise in providing better bandwidth between my desktop and my switch.  My reasoning is that, even though the wifi connection when it is operating is quite stable and is generally providing 54Mbps to my switch, if I were to bond my ethernet and my wifi connection then I'd have more like 64Mbps available and if for any reason my wifi was unstable I would still have the 10Mbps over the ethernet connection.  64Mbps when I want to upload or download between my computer and other devices on my LAN ought to be adequate.  That said, I'm not really sure why I'm not getting the 108Mbps that a 801.11n standard wifi adapter ought to give me.

That's my thinking regarding bonding.

It seems that based upon your comments, you're suggesting that I don't need ndiswrapper and could therefore uninstall it, is that right?


Thanks for your very helpful input.

---

### Post by chili555 on 2014-06-23
> It seems that based upon your comments, you're suggesting that I don't need ndiswrapper and could therefore uninstall it, is that right?Correct. ```
sudo apt-get purge ndiswrapper*
```I wonder if rt2800pci was blacklisted in the ndiswrapper process:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Is 'blacklist rt2800pci' listed? If so, remove it, proofread, save and close gedit.

Bonding is a complex process; before I undertook it, I think I'd try to troubleshoot the ethernet. It says it's connected at, not 10 Mb/s, but 100 Mb/s and reports that it's capable of gigabit speeds!> description: Ethernet interface 
        product: NetXtreme BCM5764M Gigabit Ethernet PCIe 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 10 
        serial: d0:27:88:07:63:94 
        [COLOR="#FF0000"]size: 100Mbit/s 
        capacity: 1Gbit/s [/COLOR]
        width: 64 bits 
        clock: 33MHz Do you have a switch AND a wireless router? Or...what?? I wonder if you have an extra layer of complexity that hinders performance here.

---

### Post by Steve_Par on 2014-06-23
Okay, I purged ndiswrapper, checked/etc/modprobe.d/blacklist.conf for  'blacklist rt2800pci' which wasn't listed, removed my ethernet cable and rebooted.  The result was that the computer rebooted without a network connection and the RT5392 PCIe Wireless Network Adapter was UNCLAIMED.  After I ran modprobe rt2800pci the Enable Wi-Fi line appeared unchecked (unchecked because I had the ethernet cable connected to my switch over the powerline LAN at the time I guess) in the Network Manager.  After disconnecting the ethernet network and enabling the wifi in Network Manager it connected to my wifi almost instantly.

When I say switch, what I have is a Huewai HG8245 which is a router insofar as it provides a link to the WAN over my fibre connection, but also acts as a switch insofar as it has four ethernet ports to which various devices on my LAN are connected, and in turn to the WAN over the NAT, and also it has a wireless access point operating on the B/G/N standard.

The idea for bonding principally arises due to a limitation on the Powerline LAN hardware I have which is quite old now and which carries data fairly slowly by modern standards.  Buying a wifi card was much cheaper than buying faster Powerline LAN hardware and given the new N standard, has the potential to achieve a quite high speed datalink to my HG8245 (for which, incidentally, the available firmware is rubbish, but that's another story).  For now, my idea is to get the wifi LAN working without having to run modprobe rt2800pci each time and thereafter bond the two connections.  I accept that it might be a challenge, but my guess is it should be possible.  Besides, it is by undertaking tasks such as these that I become more familiar with Ubuntu/Linux and even if I have to give up on the idea at some stage, so be it; it's not the end of the world.

---

### Post by chili555 on 2014-06-23
> For now, my idea is to get the wifi LAN working without having to run modprobe rt2800pci each time and thereafter bond the two connections. I accept that it might be a challenge, but my guess is it should be possible.I have never tried bonding, but I suspect, since there is a community document on the subject, that it's reasonably possible.

As for getting the wireless to start without human intervention, I think it's easy. First, let's assure ourselves that it isn't otherwise blacklisted:```
ls /etc/modprobe.d
```Are there any references to rt2800 or ndiswrapper? If so, please post the contents here.

Next, let's get the module to load automagically:```
sudo -i
echo rt2800pci  >>  /etc/modules
exit
```Detach the ethernet, reboot and tell us what happens.

---

### Post by Steve_Par on 2014-06-24
Ah..... > ls /etc/modprobe.d renders....

```

alsa-base.conf          blacklist.conf           blacklist-framebuffer.conf  blacklist-oss.conf           blacklist-watchdog.conf  fbdev-blacklist.conf  mlx4.conf         oss-compat.conf  vmwgfx-fbdev.conf
blacklist-ath_pci.conf  blacklist-firewire.conf  blacklist-modem.conf        blacklist-rare-network.conf  dkms.conf                iwlwifi.conf          ndiswrapper.conf  osspd.conf
```

and then.....  ndiswrapper.conf 

```

alias pci:v00001814d00003060sv00003C04sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv00003C05sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv00003C06sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv*sd*bc*sc*i* ndiswrapper
```

So, for now I've moved ndiswrapper.conf to another directory and now I will try and reboot first to see if that works.

---

### Post by Steve_Par on 2014-06-24
Well done, Chili, my good fellow!......   That was the problem.  As soon as I rebooted, after having moved Ndiswrapper.conf from /etc/modprobe.d                       both 'Enable Wifi' and 'Enable Networking' appeared in the Network Manager.  No need to do anything else.:biggrin:

So, I guess I can move on next to bonding.  I'll have a go with the community document and see how I get on.......

---

### Post by chili555 on 2014-06-24
> **Steve_Par said:**
> Well done, Chili, my good fellow!......   That was the problem.  As soon as I rebooted, after having moved Ndiswrapper.conf from /etc/modprobe.d                       both 'Enable Wifi' and 'Enable Networking' appeared in the Network Manager.  No need to do anything else.:biggrin:

So, I guess I can move on next to bonding.  I'll have a go with the community document and see how I get on.......Good news! Since you removed ndiswrapper, you can safely delete the ndiswrapper.conf file. I'd also be interested in the contents of dkms.conf; it may be related but maybe not. 

I also suspect that you will not get bonding working with Network Manager running. I would give it a shot first before we possibly remove NM. It is supposed to step aside and allow seamless management of interfaces if they are declared in /etc/network/interfaces. It usually but not perfectly works that way. Please try it first before we get out the scalpel.

---

### Post by Steve_Par on 2014-06-24
Hmmm....  Nothing exciting in dkms.conf it seems.... ```
 # modprobe information used for DKMS modules # # This is a stub file, should be edited when needed, # used by default by DKMS.
```

Okay....  I just lost a fairly lengthy message which I shall now aim to recreate....

In preparation for following [  https://help.ubuntu.com/community/UbuntuBonding]("http://https://help.ubuntu.com/community/UbuntuBonding") I tested 

> sudo stop networking again and it renders:

```
stop: Job failed while stopping
```

which seems to be described [here]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1301015")

So, I tried > sudo ifconfig wlan0 down which appeared to work as when I ran ifconfig I got:

```

eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94  
          inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:648019 (648.0 KB)  TX bytes:41697 (41.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1551593 (1.5 MB)  TX bytes:1551593 (1.5 MB)



```

(and I guess i lost my lengthy post!)

Although looking at network manager wlan still appeared to be connected.

Then I ran > sudo ifconfig wlan0 up

and ifconfig gave:
```

eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94  
          inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:652219 (652.2 KB)  TX bytes:42153 (42.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1561705 (1.5 MB)  TX bytes:1561705 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr c4:a8:1d:03:66:f2  
          inet addr:192.168.100.3  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::c6a8:1dff:fe03:66f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:746456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635240595 (635.2 MB)  TX bytes:616867995 (616.8 MB)


```

So would you think that using ifconfig up and down commands would be as good as > sudo stop networking or is there some better method of achieving that outcome?

---

### Post by chili555 on 2014-06-24
It may be as good. For interfaces configured in /etc/network/interfaces, the correct command is:```
sudo ifdown wlan0
sudo ifup wlan0
```

Stopping and starting networking is ineffective for some reason; I generally restart the computer entirely.

Your dkms.conf is all comments and therefore effectively blank. We may ignore it.

---

### Post by Steve_Par on 2014-06-24
Hmmmmm........

I note that in [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) if I am contemplating bonding mode 5 or 6 it appears that 
> **Prerequisites:**
 
Ethtool support in the base drivers for retrieving the speed of each slave. 

Examining this further I note that ethtool eth0 returns:

```
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: off
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: yes


```

Whereas ethtool wlan0 only returns:

```

Settings for wlan0:
Cannot get wake-on-lan settings: Operation not permitted
    Link detected: yes
```

May be I'm being too theoretical about this and I ought to just try it, but based on the above it seems to me that bonding mode 5 or 6 is unlikely to work with the rt2800pci driver as ethtool only returns minimal information and nothing about speed.  That would seem to suggest that I might be unable to gain the additional bandwidth that I was seeking.  Perhaps I should look at other bonding modes to see if they offer anything desirable....

---

### Post by chili555 on 2014-06-24
> based on the above it seems to me that bonding mode 5 or 6 is unlikely to work with the rt2800pci driver as ethtool only returns minimal information and nothing about speed.I agree.> May be I'm being too theoretical about this and I ought to just try it,I also agree. If either mode 5 or 6 doesn't yield a satisfactory result, you can always amend the file and try again, yes?

DISCLAIMER: I know little about bonding and am no reliable resource. There is a bondsman across from the courthouse if that helps. [http://www.speedybailbondsnj.com/images/en/bail-bonds-nj.jpg](http://www.speedybailbondsnj.com/images/en/bail-bonds-nj.jpg)

---

### Post by Steve_Par on 2014-06-24
hahaha.....   Yes, indeed.......  At least our respective talents are more equally balanced when it comes to bonding, it seems!  I think I shall try it and see what it yields.  There's no harm in that.  Even if bonding doesn't yield any useful outcome I can fairly simply untie it anyhow.  Another thought that crossed my mind, although this might be problematic, is trying to get my D-Link DWA-548 PCIe wifi card to work with the Windows native driver and see if that offers better Ethtool support.  If it does then perhaps bonding modes 5 or 6 would be possible.

---

### Post by chili555 on 2014-06-24
> is trying to get my D-Link DWA-548 PCIe wifi card to work with the Windows native driver and see if that offers better Ethtool support. If it does then perhaps bonding modes 5 or 6 would be possible.I doubt it; ethtool is built for ethernet, not wireless. Please see:```
man ethtool
```

---

### Post by Steve_Par on 2014-06-28
Okay, well here's an update.  I tried out bonding mode 0, thus far without any real success.  Having looked at the bonding [modes]("https://help.ubuntu.com/community/UbuntuBonding") (as noted and in other forums) and initially discounted modes 6 and 5, due to ethool not returning a speed value for my wifi card, I thought mode 0 looked like the best alternative.  Anyhow, mode 0 didn't work, at least the way I had it configured it didn't.

Firstly, with 'Enable Networking' disabled in network manager                          > cat /proc/net/bonding/bond0

   yielded:

                        ```
Bonding Mode: load balancing (round-robin)  

 MII Status: up  
 MII Polling Interval (ms): 100  
 Up Delay (ms): 0  
 Down Delay (ms): 0  
 

 Slave Interface: eth0  
 MII Status: up  
 Speed: 100 Mbps  
 Duplex: full  
 Link Failure Count: 0  
 Permanent HW addr: d0:27:88:07:63:94  
 Slave queue ID: 0  
 

 Slave Interface: wlan0  
 MII Status: down  
 Speed: Unknown  
 Duplex: Unknown  
 Link Failure Count: 0  
 Permanent HW addr: c4:a8:1d:03:66:f2  
 Slave queue ID: 0  

```

I tried                                                > sudo modprobe rt2800pci  

     in a futile effort to get the wifi driver to load.  

> cat /proc/net/bonding/bond0

 yielded:

                          ```
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)  

 

 Bonding Mode: load balancing (round-robin)  
 MII Status: up  
 MII Polling Interval (ms): 100  
 Up Delay (ms): 0  
 Down Delay (ms): 0  
 

 Slave Interface: eth0  
 MII Status: up  
 Speed: 100 Mbps  
 Duplex: full  
 Link Failure Count: 0  
 Permanent HW addr: d0:27:88:07:63:94  
 Slave queue ID: 0  
 

 Slave Interface: wlan0  
 MII Status: down  
 Speed: Unknown  
 Duplex: Unknown  
 Link Failure Count: 0  
 Permanent HW addr: c4:a8:1d:03:66:f2  
 Slave queue ID: 0  

```

I tried to ping [www.google.com]("http://www.google.com") to see if I had any WAN connectivity and it returned:

                        > ping: unknown host [www.google.com]("http://www.google.com")  



I then enabled networking in network manager and obtained the following results:

                        ```
cat /proc/net/bonding/bond0  

 Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)  
 

 Bonding Mode: load balancing (round-robin)  
 MII Status: up  
 MII Polling Interval (ms): 100  
 Up Delay (ms): 0  
 Down Delay (ms): 0  
 

 Slave Interface: eth0  
 MII Status: up  
 Speed: 100 Mbps  
 Duplex: full  
 Link Failure Count: 0  
 Permanent HW addr: d0:27:88:07:63:94  
 Slave queue ID: 0  
 

 Slave Interface: wlan0  
 MII Status: up  
 Speed: Unknown  
 Duplex: Unknown  
 Link Failure Count: 0  
 Permanent HW addr: c4:a8:1d:03:66:f2  
 Slave queue ID: 0  

```

And then ifconfig gave:

                        ```
bond0     Link encap:Ethernet  HWaddr d0:27:88:07:63:94   

           inet addr:192.168.100.5  Bcast:192.168.100.255  Mask:255.255.255.0  
           inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link  
           UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1  
           RX packets:689 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:151 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:84077 (84.0 KB)  TX bytes:21376 (21.3 KB)  
 

 eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94   
           UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1  
           RX packets:580 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:94 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:59159 (59.1 KB)  TX bytes:13822 (13.8 KB)  
           Interrupt:17  
   
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:1469 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1469 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:129254 (129.2 KB)  TX bytes:129254 (129.2 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr d0:27:88:07:63:94   
           inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0  
           UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1  
           RX packets:109 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:57 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:24918 (24.9 KB)  TX bytes:7554 (7.5 KB)  

```

I then disabled networking in network manager and ifconfig gave:-

                        ```
bond0     Link encap:Ethernet  HWaddr d0:27:88:07:63:94   

           inet addr:192.168.100.5  Bcast:192.168.100.255  Mask:255.255.255.0  
           inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link  
           UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1  
           RX packets:599 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:105 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:60984 (60.9 KB)  TX bytes:15428 (15.4 KB)  
 

 eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94   
           UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1  
           RX packets:599 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:105 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:60984 (60.9 KB)  TX bytes:15428 (15.4 KB)  
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:1474 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:129774 (129.7 KB)  TX bytes:129774 (129.7 KB)  
 

  
```

There is still a lot more I can do to try and get this to work.  For example, i read that someone else had better luck using bonding mode 2, which appears to be a reasonable option for me too as I am looking for both fault tolerance and load balancing.

Anyhow, i shall turn my attention back to this soon once I have a bit more time.  In the meantime, should anyone have any suggestions, I'd be delighted to take account of them....  ;)

---

### Post by chili555 on 2014-06-28
Network Manager is designed to prefer ethernet if it's available and turn off wireless. That's why I speculated above that you may not be able to get bonding going with NM installed. There is a file that is supposed to allow interfaces listed in /etc/network/interfaces to be ignored by NM. It is /etc/NetworkManager/NetworkManager.conf. In a perfect world, if the stars are aligned and there aren't any solar flares, this setting requires NM to defer to /etc/network/interfaces:```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
[COLOR="#FF0000"]managed=false[/COLOR]
```In plain language, that means that NM will ***not*** manage interfaces declared in /etc/network/interfaces.

Make sure that your setting is also 'managed=false'; if you need to change it, restart NM:```
sudo service network-manager restart
```You might also try bonding with and without Enable Networking checked at the NM icon.

---

