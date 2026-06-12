---
title: "Help: Prism 2.5 Wavelan with WPA encryption and hostap"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Sementis on 2008-01-11
Hi there,

I have trouble getting my Prism 2.5 Wavelan (onboard) to work with the local WPA-protected wireless network. 
After hours trying out several how-to's I dumped the recent Xubuntu system and installed a fresh one.

As introduction: I am a beginner with Ubuntu/Xubuntu, but am trained (during countless hours of searching forums and following howto's) in pasting commands ;)

One day I hope to become an Ubuntu-pro and help people like me (the now me)!

Here the facts:
Thinkpad X22 (recently bought with no OS)
Xubuntu 7.04 with actual updates 
Prism 2.5 Wavelan chip

What i have done so far: 

- blacklisted (editing /etc/modlist.d/blacklist) hermes, orinoco_pci, orinoco, prism2_pci to force the kernel to use the hostap driver (needed for connecting WPA networks via Prism 2.5) for Prism 2.5.

- installed network-manager and network-manager-gnome



Here are some pastes from lshw -C network, iwconfig, ifconfig and /etc/network/interfaces

lshw -C network: > 
*-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: wifi0
       version: 01
       serial: 00:20:e0:89:17:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.1.1 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:f0000000-f0000fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:83:03:4e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:c0200000-c0200fff ioport:8000-803f irq:11

iwconfig:> 
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:7   Missed beacon:0

ifconfig:> 
eth0      Link encap:Ethernet  HWaddr 00:D0:59:83:03:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:D0:59:83:03:4E  
          inet addr:169.254.4.158  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148510 (145.0 KiB)  TX bytes:148510 (145.0 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-20-E0-89-17-8A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

wlan1     Link encap:Ethernet  HWaddr 00:20:E0:89:17:8A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

/etc/network/interfaces: > 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





What do I have to do now? Please help me for I'm keen on continuing my experiment "ubuntu is outclassing windows" :)

Greetings!
Sem

---

### Post by wieman01 on 2008-01-11
Question: After blacklisting these modules/drivers, what did you install? Another driver or 'ndiswrapper'? 

Thing is blacklisting basically disables your card, so unless you plan to make use of an alternative solution, you render your system 'useless' if you know what I mean. So what driver do you plan to use?

What is the exact name of your onboard wireless adapter? Do you find it somewhere on this list?

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

---

### Post by Sementis on 2008-01-11
As far as i can see (lsmod) xubuntu loaded hostap_pci and hostap after my blacklisting. 

The exact name of the device would be:

description: Wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation

I didn't install ndiswrapper. 
I hope I can manage your sticky howto: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

The problem is: unfortunately, already on your 1. point I 
(Prism 2.5 wavelan + Xubuntu 7.04) have to surrender:

iwconfig:
> lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

wifi0 IEEE 802.11b ESSID:"" Nickname:""
Mode:Managed Frequency:2.427 GHz Access Point: None 
Bit Rate:2 Mb/s Sensitivity=1/3 
Retry limit:8 RTS thr:off Fragment thr:off
Power Management:off

wlan1 IEEE 802.11b ESSID:"" Nickname:""
Mode:Managed Frequency:2.427 GHz Access Point: None 
Bit Rate:2 Mb/s Sensitivity=1/3 
Retry limit:8 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/92 Signal level=-90 dBm Noise level=-90 dBm
Rx invalid nwid:0 Rx invalid crypt:1 Rx invalid frag:0
Tx excessive retries:11 Invalid misc:7 Missed beacon:0 

iwlist scan: 
> lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

irda0 Interface doesn't support scanning.

wifi0 No scan results
wlan1 No scan results

---

### Post by wieman01 on 2008-01-11
My sticky won't help you unless the scan yields any results. No scan results generally mean the device isn't working.
> description: Wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
...that's the chipset, however, do you know the manufacturer? Trying to find it on "ndiswrapper's" website. Just to see how we get it working.

---

### Post by Sementis on 2008-01-11
At [1] I found Chipset: Harris Semiconductor Prism 2.5.
Could'nt find neither Harris nor Intersil with Prism 2.5 in ndiswrapper-list [2].

But [1] says that hostap is the preferable driver.
Does this help anyway?

[1] [http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_with_Modem](http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_with_Modem)
[2] [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by wieman01 on 2008-01-11
Do you happen to have a copy of the Windows driver? If so, please attach it here so that I can take a look at it.

---

### Post by Sementis on 2008-01-12
With the laptop no Driver-CD was delivered, so I clusty'd a bit:

[http://www.netstumbler.org/f48/new-prism-2-5-3-win9x-2k-xp-drivers-wpa-support-11366/](http://www.netstumbler.org/f48/new-prism-2-5-3-win9x-2k-xp-drivers-wpa-support-11366/)

---

### Post by wieman01 on 2008-01-12
I still don't understand what manufacturer or vendor your hardware is. Without that piece of information we are stumped. 

Any idea? There must be a driver somewhere...

---

### Post by Sementis on 2008-01-12
It has to be either Harris Semiconductor or Intersil Corporation.

sudo lspci shows: 02:05.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

---

### Post by wieman01 on 2008-01-12
I can't find any drivers for it. Intersil seems to be the chipmaker, not the vendor (e.g. Linksys, Netgear). You said you don't have any CD that came with the PC, but is there a chance that you find anything on the vendor's website or something like that?

We really need to get hold of the Windows driver to get your card working...

---

### Post by ilovebsod on 2008-01-16
Hi, sorry to thread hijack, but I'm having similar problems with the same chipset/wifi card.

I have a Fujitsu p1120 Lifebook w/ the Intersil Prism 2.5 Wavelan.

I updated the firmware to the most recent, stable version that supports WPA and I still can't get connected to any WPA networks in Xubuntu.  I am able to connect in Windows XP.

Here are the Windows drivers from Fujitsu's website

[http://ilovebsod.com/wp-content/uploads/2008/01/fujitsuintersiltar.gz](http://ilovebsod.com/wp-content/uploads/2008/01/fujitsuintersiltar.gz)

Also here is my original post

[http://ubuntuforums.org/showthread.php?t=663177](http://ubuntuforums.org/showthread.php?t=663177)

anything you can do to help would be greatly appreciated.

---

### Post by ilovebsod on 2008-01-17
did I jump on this too late?

---

### Post by Doctor Device on 2008-01-17
I have the exact same card as the original poster in my X24. I've not been able to find any mention of it on the ndiswrapper webpage, (a search shows nothing for even the word "prism").

I know the windows driver can be found [_here_](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-41929) ,assuming the link works.

I'm glad it sounds like somebody can get this card working in some fashion under linux. it gives me hope that I'm not staring down the impossible in trying to make my card connect at all.

edit: I should have pointed out that you'll have to manually extract the driver files themselves from the executable.

---

### Post by ilovebsod on 2008-01-18
now this is strange.  I just installed Ubuntu (via PXE, as I did w/ Xubuntu) and I don't even have the option to select WPA when I click on the Net Manager icon and select 'other wireless networks'

this really sucks.  I think I might have to stick with XP on this laptop

---

### Post by ilovebsod on 2008-01-20
bumping one last time in hopes of some help :KS

---

### Post by wieman01 on 2008-01-21
> **ilovebsod said:**
> bumping one last time in hopes of some help :KS
Does [WICD]("http://wicd.sourceforge.net/") work for you? If not, 'ndiswrapper' might do the job, although I like to avoid it...

---

### Post by gustl on 2008-01-22
Hi,

I am experiencing similar problems with the same wlan card on a x30.
Did you try the firmware flash?
In order for the hostap driver to support wpa/wpa2 you need firmware version 1.7.4

```

root@ulaf:~# hostap_diag wlan0
Host AP driver diagnostics information for 'wlan0'

NICID: id=0x8013 v1.0.0 (PRISM II (2.5) Mini-PCI (SST parallel flash))
PRIID: id=0x0015 v1.1.1
STAID: id=0x001f v1.7.4 (station firmware)

```

With my little linux knowledge I managed to to the firmware upfdate as described here:
[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

But I didn't achieve any further results...Maybe you try ;-)

---

### Post by ilovebsod on 2008-01-22
yeah, I'm on 1.8.2.

I haven't tried WICD yet.  I'll give it a go and report back.

---

### Post by gustl on 2008-01-23
> **ilovebsod said:**
> 
I haven't tried WICD yet.  I'll give it a go and report back.

that would be great, just to know if it works for you.

---

### Post by ilovebsod on 2008-01-23
WICD killed my ability to access anything over the network port(s).

installed it through synaptic, it uninstalled network-manager.  install completed and I could no longer access the internet over my wired network.  tried rebooting (yeah I know that's not necessary, but old habit), nothing.  

went back into synaptic and removed it, reinstalled network-manager and network-manager-gnome.  right as raid again, but still can't get on WiFi w/ WPA.

---

### Post by wieman01 on 2008-01-24
Then you have no choice but to replace the current driver with 'ndiswrapper'. Do you know what that is?

---

### Post by ilovebsod on 2008-01-24
from what I've gathered it will allow me to use a windows driver in place of the driver Ubuntu provides

I found this article

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

I'll read through it and try it.

Thanks for all your help.

---

### Post by wieman01 on 2008-01-24
> **ilovebsod said:**
> from what I've gathered it will allow me to use a windows driver in place of the driver Ubuntu provides

I found this article

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

I'll read through it and try it.

Thanks for all your help.
Exactly. If that fails, I have my own 'ndiswrapper' tutorial (see signature: Ralink). It should work for you as well.

---

