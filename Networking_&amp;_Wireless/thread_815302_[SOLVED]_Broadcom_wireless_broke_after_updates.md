---
title: "[SOLVED] Broadcom wireless broke after updates"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by crjackson on 2008-06-01
Today I installed several updates on my laptop (emachinesM6809) with a broadcom wireless card.  Now this card was working just fine using fwcutter but after the update it lost the card and I couldn't get it working again.

So I used ndiswrapper and the windows driver and it's working (somewhat).  Now, it won't always connect.  I have to insert my pcmcia wireless card to get a connection.  Then, it's like it learns after a few minutes and the Broadcom card starts connecting.

What can I do to make this Broadcom card connect everytime like it used to?

Thanks...

---

### Post by bucknasty2134 on 2008-06-01
Bump

---

### Post by crjackson on 2008-06-01
Anyone?

---

### Post by crjackson on 2008-06-02
Standing by for suggestions...

---

### Post by Ayuthia on 2008-06-03
> **crjackson said:**
> Today I installed several updates on my laptop (emachinesM6809) with a broadcom wireless card.  Now this card was working just fine using fwcutter but after the update it lost the card and I couldn't get it working again.

So I used ndiswrapper and the windows driver and it's working (somewhat).  Now, it won't always connect.  I have to insert my pcmcia wireless card to get a connection.  Then, it's like it learns after a few minutes and the Broadcom card starts connecting.

What can I do to make this Broadcom card connect everytime like it used to?

Thanks...
Not for sure if I can help or not, but can you post the following:
```
uname -r
lshw -C network
```I think the b43 driver is mainly affected by kernel updates.

---

### Post by vexingmodstwo on 2008-06-03
One word:  wifiradar

I'm noticing a trend with all these wireless issues and it seems to be deeper than just the card and drivers.  There's something going on with the DHCP stuff.

Anyway, I did all the how to's and nothing would work until I replaced NM with wifiradar and manually configured the connection.

---

### Post by crjackson on 2008-06-03
> **Ayuthia said:**
> Not for sure if I can help or not, but can you post the following:
```
uname -r
lshw -C network
```I think the b43 driver is mainly affected by kernel updates.

Here is the output of the code you listed.  Keep in mind I am also using a pcmcia ralink card until I get this sorted, so you can ignore the last card.

Also I currently configured the card using ndiswrapper since fwcutter doesn't show up anymore.  Sometimes after being connected using the ralink card, the broadcom will connect but never from a reboot or just on it's own.  It has to be connected to the internet using another device first.  It's like the connection has to be established first and then sometimes the broadcom will decide to work.

```
charles@charles-laptop:~$ uname -r
2.6.24-17-generic
charles@charles-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:b4:e1:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:13:1c:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:60:d4:ec:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.106 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
charles@charles-laptop:~$
```

---

### Post by vexingmodstwo on 2008-06-03
You look like you're in the same boat I was in two days ago.

I hate to sound like a broken record but I would really consider wifiradar if I were you.  I had the same kind of stuff going on with Network Manager and then with WICD.  wifiradar found the connection and I was wireless in seconds.

---

### Post by crjackson on 2008-06-03
> **vexingmodstwo said:**
> You look like you're in the same boat I was in two days ago.

I hate to sound like a broken record but I would really consider wifiradar if I were you.  I had the same kind of stuff going on with Network Manager and then with WICD.  wifiradar found the connection and I was wireless in seconds.

Does Wifirader support roaming?

---

### Post by vexingmodstwo on 2008-06-03
> **crjackson said:**
> Does Wifirader support roaming?

I believe it does.

---

### Post by crjackson on 2008-06-03
> **vexingmodstwo said:**
> I believe it does.

I installed it.  It didn't really do anything for me though.

---

### Post by vexingmodstwo on 2008-06-03
> **crjackson said:**
> I installed it.  It didn't really do anything for me though.

Did you try a manual configuration for the wireless connection instead of the AutoDHCP?

---

### Post by crjackson on 2008-06-03
> **vexingmodstwo said:**
> Did you try a manual configuration for the wireless connection instead of the AutoDHCP?

Yes.  I didn't really have much time to tinker around before going to work though.  I'll try again after work or tomorrow.  I'm considering just buying an intel card from ebay since they have good support.

---

### Post by smsmith050 on 2008-06-03
I have no option to enable wireless in the network-manager-applet. 
I have wireless 

30:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

iwconfig sees the wireless

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw -C network

  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:4e:59:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

I can run iwlist wlan0 scanning and see networks near me.

but the network-manager-applet never sees the wireless interface

/proc/net# more wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000    0     0     0        0      0      0      0      0        0

uname -a
Linux ubuntu 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

Can anyone tell me how to make the network-manager-applet see the wireless interface?

thanks

---

### Post by smsmith050 on 2008-06-03
I said network-manager-applet but it really is nm-applet.
nm-applet does not see my wireless card wlan0
wireless was working fine until I tried to connect to work using vpn.

---

### Post by crjackson on 2008-06-04
> **vexingmodstwo said:**
> Did you try a manual configuration for the wireless connection instead of the AutoDHCP?

More tinkering...  Still no change...  I got some kernel updates today but they made do difference.

---

### Post by crjackson on 2008-06-05
Well I don't have time to wait for a kernel fix on this one.  I ordered an intel pro wireless mini pci card (2200bg) a few minutes ago.  I'll use the pcmcia card until it gets here.  I pulled one from my wife's laptop and it works better on Ubuntu than the broadcom ever did.

---

### Post by crjackson on 2008-07-02
Issues solved by installing an Intel Wireless Card.

---

