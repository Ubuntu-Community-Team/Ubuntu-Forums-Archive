---
title: "Wireless is driving me nuts..........."
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by birddawg on 2008-02-16
Thanks in advance, any help is greatly appreciated.

I have an EdiMax 7126 wireless PCI card installed in my box.  On the card itself is the RTL8180 chipset, says so right on the top.  When I type lshw -C network, I see the card at wlan0 with driver set to the rtl8180 driver.  I can set the essid and ip and gateway.
From all apperances, it looks as if this card is working.
However, when I ping an address, no joy.  
My router works ok, I'm typing this post on my windows box now.

What should I look for, info to post?  Is this card or driver buggie?

Thanks

---

### Post by mrsteveman1 on 2008-02-16
Can you ping the router?

---

### Post by birddawg on 2008-02-16
No, I cannot ping the router.

I'm about ready to give up on this card, but I can't find  a truly compatable wireless nic.  Not saying there is not one, I just don't what to look for.
Thanks,

---

### Post by mrsteveman1 on 2008-02-16
Does dmesg show any errors?

Is this driver one that came with ubuntu or did you compile it?

---

### Post by birddawg on 2008-02-16
The driver came with ubuntu. It's a fresh install, 

I get "Destination Host Unreachable"

Thanks

---

### Post by mrsteveman1 on 2008-02-16
Ok, check your dmesg log for any errors (theyll be obvious i think).

Also post the results of the following commands:

```
sudo arp
sudo ethtool -S wlan0
sudo route
```

---

### Post by birddawg on 2008-02-16
thanks  mrsteve
nothing returned on sudo arp.
Here's the rest.
looks like the card reset twice.



user1@ubuntu:~/Desktop/rtl8180-0.21$ sudo arp
[sudo] password for user1:
user1@ubuntu:~/Desktop/rtl8180-0.21$ sudo ethtool -S wlan0
Cannot get driver information: Operation not supported
user1@ubuntu:~/Desktop/rtl8180-0.21$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
user1@ubuntu:~/Desktop/rtl8180-0.21$ 

Feb 16 14:50:11 ubuntu kernel: [  141.994726] rtl8180: Bringing up iface
Feb 16 14:50:11 ubuntu kernel: [  142.202749] rtl8180: Card successfully reset
Feb 16 14:50:12 ubuntu kernel: [  142.581637] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 16 14:50:12 ubuntu kernel: [  142.595288] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 16 14:50:12 ubuntu kernel: [  142.993043] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 16 14:50:48 ubuntu kernel: [  179.292873] rtl8180: Bringing up iface
Feb 16 14:50:49 ubuntu kernel: [  179.500889] rtl8180: Card successfully reset
Feb 16 14:50:49 ubuntu kernel: [  179.884686] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 16 14:57:40 ubuntu kernel: [  590.470670] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 16 14:57:41 ubuntu kernel: [  590.833899] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 16 15:08:22 ubuntu -- MARK --
Feb 16 15:28:22 ubuntu -- MARK --
Feb 16 15:48:22 ubuntu -- MARK --
Feb 16 16:08:22 ubuntu -- MARK --
Feb 16 16:28:22 ubuntu -- MARK --
Feb 16 16:48:22 ubuntu -- MARK --
Feb 16 17:08:22 ubuntu -- MARK --
Feb 16 17:28:22 ubuntu -- MARK --
Feb 16 17:48:22 ubuntu -- MARK --
Feb 16 18:08:22 ubuntu -- MARK --
Feb 16 18:28:22 ubuntu -- MARK --
Feb 16 18:33:54 ubuntu kernel: [13542.221748] usb 5-7.1: new high speed USB device using ehci_hcd and address 5
Feb 16 18:33:54 ubuntu kernel: [13542.330533] usb 5-7.1: configuration #1 chosen from 1 choice
Feb 16 18:33:54 ubuntu kernel: [13542.331278] scsi5 : SCSI emulation for USB Mass Storage devices
Feb 16 18:33:59 ubuntu kernel: [13547.321861] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.4  PQ: 0 ANSI: 2
Feb 16 18:33:59 ubuntu kernel: [13547.323616] sd 5:0:0:0: [sdf] 4001760 512-byte hardware sectors (2049 MB)
Feb 16 18:33:59 ubuntu kernel: [13547.324228] sd 5:0:0:0: [sdf] Write Protect is off
Feb 16 18:33:59 ubuntu kernel: [13547.326222] sd 5:0:0:0: [sdf] 4001760 512-byte hardware sectors (2049 MB)
Feb 16 18:33:59 ubuntu kernel: [13547.326845] sd 5:0:0:0: [sdf] Write Protect is off
Feb 16 18:33:59 ubuntu kernel: [13547.326860]  sdf: sdf1
Feb 16 18:33:59 ubuntu kernel: [13547.327944] sd 5:0:0:0: [sdf] Attached SCSI removable disk
Feb 16 18:33:59 ubuntu kernel: [13547.328010] sd 5:0:0:0: Attached scsi generic sg6 type 0
Feb 16 18:48:22 ubuntu -- MARK --
Feb 16 19:08:22 ubuntu -- MARK --

---

### Post by mrsteveman1 on 2008-02-16
On your router, theres a light that shows wireless activity right? 

Does that light flash if you initiate a ping (to anywhere) from the linux machine?

I'm trying to figure out if the machine is even sending ethernet frames at all, since arp doesn't show any MAC addresses its obviously not getting those when it needs to ping another machine, and since ethtool wasn't able to pull statistics from the driver i can't tell if its getting frame errors or if they aren't even sending.

Since the driver is at least coming up, layer 2 (ethernet frames, MAC addys etc) should work, but it does look like either the device reset or the driver reset itself. This is a built in device right? not a USB stick?

Did you have to install firmware for this device yourself?

Is wifi0 the physical device? or is it something like eth1? You can check by doing ifconfig -a

Try running ethtool -t wifi0 to see if the driver will respond to a self test request. It might be that this driver doesn't support ethtool at all.

---

### Post by birddawg on 2008-02-16
mrsteve,  I think maybe the light on my router is blinking when I ping it.  It's hard to tell because when I pinged, out of 35 or so attempts, I saw only one or maybe two blinks. 
And yes the card is built in, it's a PCI card and no I did not install the firmware.
The device is wlan0
I found a rtl8180 file on the net, copied it over from my thumb drive, extracted it and read the reame file.  That what the rtl8180-0.21 prompt is for.  I tried to make the makefile, but it crashed with several errors.  Thats as far as that got.  

here is another cut and paste


user1@ubuntu:~/Desktop/rtl8180-0.21$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:6C:6C:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xac00 Memory:ff8e0000-ff900000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8094 (7.9 KB)  TX bytes:8094 (7.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:24:72:93  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:885068 (864.3 KB)
          Interrupt:20 Memory:e09bec00-e09bed00 


user1@ubuntu:~/Desktop/rtl8180-0.21$ sudo ethtool -t wlan0
Cannot get driver information: Operation not supported

---

### Post by birddawg on 2008-02-16
by the way, here is screen capture from the ping


user1@ubuntu:~/Desktop/rtl8180-0.21$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.114 icmp_seq=1 Destination Host Unreachable
From 192.168.1.114 icmp_seq=2 Destination Host Unreachable
From 192.168.1.114 icmp_seq=3 Destination Host Unreachable
From 192.168.1.114 icmp_seq=4 Destination Host Unreachable
From 192.168.1.114 icmp_seq=5 Destination Host Unreachable
From 192.168.1.114 icmp_seq=6 Destination Host Unreachable
From 192.168.1.114 icmp_seq=7 Destination Host Unreachable
From 192.168.1.114 icmp_seq=8 Destination Host Unreachable
From 192.168.1.114 icmp_seq=9 Destination Host Unreachable
From 192.168.1.114 icmp_seq=10 Destination Host Unreachable
From 192.168.1.114 icmp_seq=11 Destination Host Unreachable
From 192.168.1.114 icmp_seq=12 Destination Host Unreachable
From 192.168.1.114 icmp_seq=13 Destination Host Unreachable
From 192.168.1.114 icmp_seq=14 Destination Host Unreachable
From 192.168.1.114 icmp_seq=15 Destination Host Unreachable
From 192.168.1.114 icmp_seq=16 Destination Host Unreachable
From 192.168.1.114 icmp_seq=17 Destination Host Unreachable
From 192.168.1.114 icmp_seq=18 Destination Host Unreachable
From 192.168.1.114 icmp_seq=19 Destination Host Unreachable
From 192.168.1.114 icmp_seq=20 Destination Host Unreachable
From 192.168.1.114 icmp_seq=21 Destination Host Unreachable
From 192.168.1.114 icmp_seq=22 Destination Host Unreachable
From 192.168.1.114 icmp_seq=23 Destination Host Unreachable
From 192.168.1.114 icmp_seq=24 Destination Host Unreachable
From 192.168.1.114 icmp_seq=25 Destination Host Unreachable
From 192.168.1.114 icmp_seq=26 Destination Host Unreachable
From 192.168.1.114 icmp_seq=27 Destination Host Unreachable
From 192.168.1.114 icmp_seq=28 Destination Host Unreachable
From 192.168.1.114 icmp_seq=29 Destination Host Unreachable
From 192.168.1.114 icmp_seq=30 Destination Host Unreachable
From 192.168.1.114 icmp_seq=31 Destination Host Unreachable
From 192.168.1.114 icmp_seq=32 Destination Host Unreachable
From 192.168.1.114 icmp_seq=33 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
34 packets transmitted, 0 received, +33 errors, 100% packet loss, time 33089ms
, pipe 3

---

### Post by mrsteveman1 on 2008-02-16
The network isn't encrypted is it? Its an open access point?

Does sudo iwlist scan return anything at all?

Since ping doesnt work at the moment im wondering if the device is even broadcasting at all. scanning should tell you that at the most basic level, if it cant find an AP then its definitely the driver/firmware acting funny.

---

### Post by Jorgo on 2008-02-16
I had a similar problem with my D-Link wireless PCI card.  It turned out it wasn't connecting to the acess point.

Try iwconfig and see if an access point is shown.  If not you can specify one using iwconfig *interface* ap *access point mac*.

To find out what the mac of the access point was, I used iwlist ap.  It came up with a few and I assumed the one with the best signal strength was mine (turned out I was correct).  Hope this helps.

---

### Post by birddawg on 2008-02-16
mrsteve,
here is the results for iwlist
The net is open and not encrypted.

user1@ubuntu:~/Desktop$ sudo iwlist
[sudo] password for user1:
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
user@ubuntu:~/Desktop$

---

### Post by mrsteveman1 on 2008-02-16
iwlist scan

or

iwlist wlan0 scan

---

### Post by birddawg on 2008-02-16
Thanks again mrsteve

here you go



user1@ubuntu:~/Desktop$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

user1@ubuntu:~/Desktop$ iwlist wlan0 scan
wlan0     No scan results

user1@ubuntu:~/Desktop$

---

### Post by mrsteveman1 on 2008-02-16
No scan results means the device isnt even returning radio information.

Your best bet is to see if there is an updated driver you can compile and use for this chip, as i understand it you are using the one which came with ubuntu, there is likely a better driver available.

I believe firmware is also required (though if you don't have the firmware installed there should have been a message in dmesg about it).

Where did you download the 8180 file you said you found?

---

### Post by birddawg on 2008-02-16
I downloaded the file from here
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)
There is a link for the actual file itself.

Like I said earlier, the make file crashed.  I'll try again

At the bottom of the page you'll see this link
[http://sourceforge.net/projects/rtl8180-sa2400](http://sourceforge.net/projects/rtl8180-sa2400)

It's dated for 2005 which makes me think it would not work anyway.

What do you think?
Thanks again for your help.

---

### Post by mrsteveman1 on 2008-02-16
The driver already on your system is probably newer than the external driver, my guess is that development for this chipsets driver is being done by the kernel developers themselves now, which presents a few problems.

If the current kernel driver doesn't work well and you can't download a newer one to compile and use, your only options are to use a new kernel, hope the driver from the new kernel can be used on your kernel, or hope the ubuntu developers backport the driver (which is what they should do, but sometimes can't).

I do notice there are patches for the driver you mentioned, aircracks site has patches for it but im not sure if the patch is intended to fix anything.

The aircrack page is [here]("http://www.aircrack-ng.org/doku.php?id=r8180-sa2400")

It might also be possible to use the newer driver on the old kernel, which i will look into if i can't find a newer driver somewhere.

---

### Post by mrsteveman1 on 2008-02-17
Update a bit: The native 8180 driver doesn't use firmware at all so thats not a problem. The driver is being developed in the kernel now, so the most up to date version is in the newest kernel source. I'm working on compiling this newer driver against the older source from ubuntu right now.

Are you using fiesty or gutsy?

Regardless of if i can make the new driver work on the stock ubuntu kernel, have you tried using NDISwrapper? It may be the best option for the moment.

I also found this page here about upgrading to the newest kernel: [http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755"). This would give you the new driver without having to update the entire system.

---

### Post by birddawg on 2008-02-18
mrsteve,
Thanks for the advice, I upgraded the kernel per instruction in the above link. 

now I get this

user1@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:0c:f1:6c:6c:59
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.1.113 latency=0 mingnt=255 module=e1000 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
user1@ubuntu:~$ 


Notice the network unclaimed.  When I type the command ifconfig
I get


user1@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user1@ubuntu:~$ 


From what I've read, the network unclaimed is because no driver is claiming the this hardware.  Could it be that this hardware will not be supported under the new hardy kernel.  
By the way, you asked earlier what version I was using.  I am using 7.1 Gutsy.

Thanks again,

---

### Post by mrsteveman1 on 2008-02-18
I know there are a lot of problems with this driver, so at this point you are better off using ndiswrapper.

Do you have a windows driver for this card?

---

### Post by birddawg on 2008-02-18
Thanks, 
I've ordered another wireless card,  and I think it will have the rt2500 chip set; so we'll see.

Can you reccomend a wireless nic card that works?  I hate to put you the spot by asking,  sorry.  Maybe I should look at all I have and just buy what I don't, hehe ;-)

I think I'm going to give up this card entirely.

---

### Post by mrsteveman1 on 2008-02-19
Best advice with Linux tends to be to buy cards with atheros chipsets, because Atheros has done pretty well supporting Linux directly.

As for which model/revision of specific manufacturers cards USE atheros chipsets, that changes constantly. The madwifi site has a list of current model numbers that use atheros chipsets, but note that even if the model number on a card is the same the chipset could be different because they change chipsets constantly.

---

