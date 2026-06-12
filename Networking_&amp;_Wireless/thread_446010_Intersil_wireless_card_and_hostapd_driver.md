---
title: "Intersil wireless card and hostapd driver"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by helgi on 2007-05-16
Trying to keep my sanity here.  I got Xubuntu 7.04. An HP nx9000.

Problem: Trying to get my wireless card to work which is: Intersil Prism2.5 wavelan chipset (rev 01)

As I understand from the document I have read I need to install an hostpad driver.

I have downloaded the driver and it is a tar file.

I use the command in terminal:

[PHP]tar xvjf hostapd-0.5.7.tar[/PHP]

Output i get:

[PHP]bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous error [/PHP]

So my problem is basicaly that I don't know how to install a tar file. All tips and recomendation on how to make my wireless card work would be highly appreciated

I am an absolut beginner please help. And please note that am not at all familiar with terminal commands.

---

### Post by chili555 on 2007-05-16
Actually, hostap is already installed! Good news, eh? Plug that card in and do these commands separately in a terminal:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```*lsmod* means list all the modules you have loaded; | means pipe the output through another command; *grep* means look for the words...

The problem is usually that Feisty loads *too many* modules and they end up fighting for world domination instead of downloading mp3s, torrents and updates. You have to kick prism2 out. *sudo gedit /etc/modprobe.d/blacklist* to add the separate line:```
blacklist   prism2_<whatever_you_found>
```It may be prism2_cs or prism2_pci or otherwise.

Reboot and post back so we'll know if we guessed right!

---

### Post by helgi on 2007-05-16
Well that probably would have worked if I hadn't previously been screwing with things.

From I thread I found I thought all I had to do was entering this:
The thread: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

```
$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r prism2_pci
$ sudo modprobe orinoco_pci
```

lsmod gave me no output.

Im guessing the -r in the code means "remove" so I have apparently removed the hostap driver or what?

---

### Post by helgi on 2007-05-16
Do you think I should run the above modprobe commands with -i instead of the -r to undo what I have done?

---

### Post by chili555 on 2007-05-16
I am certain you are correct; these don't show up under *lsmod* because you have removed them. But this is only temporary. On reboot, all these will reload, including the renegade prism2_pci. Please *sudo gedit /etc/modprobe.d/blacklist* to add a new line:```
blacklist  prism2_pci
```Save and close gedit and reboot. You should be good.

Use *nano* if you don't have gedit.

---

### Post by helgi on 2007-05-17
Hey great! We seem to be on the right track.

After I blacklisted and re-booted I got this out of iwconfig:

```
boston@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:" "  Nickname:""
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s   
          Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      IEEE 802.11b  ESSID:" "  Nickname:""
          Mode:Managed  Access Point: Not-Associated   Bit Rate:2 Mb/s   
          Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Previously I had no wireless extention on all of them.

I've tried going into "Network" and enebled the wifi connection(i've tried wifi0 and eth0), but it doesn't stay enabled and doesn't pick up any signal it appeares.

Remember I have xubuntu, do I need to install wifi-radar or network manager. What about ndiswrapper(or what it's called)?

Thanks for staying with me on this.

---

### Post by chili555 on 2007-05-17
Feisty (7.04) installs Network Manager by default; It has its problems, as you may see on this forum; let's try to configure this manually before we go any farther. Walk before run, as it were.

It's a bit unusual to get two interfaces, but not unheard of; the same for wireless being eth0 instead of eth1. Let's see if we can connect with eth0. Please show us the output of:```
sudo iwlist eth0 scan
```We're getting there. Thanks.

---

### Post by helgi on 2007-05-17
This is what I got:
```
boston@ubuntu:~$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning : Network is down
```

Same results when I did this for wifi0.

---

### Post by chili555 on 2007-05-18
Ole Chili smells somethin' fishy. Time to delve deeper. Please let me see```
sudo lshw -C network
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```

This is very mysterious. Any Prism 2.5 should grab eth1 and monitor.

---

### Post by helgi on 2007-05-18
```
boston@ubuntu:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wifi0
       version: 01
       serial: 00:02:8a:9f:d5:4e
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d000b000-d000bfff irq:10
  *-network:1 DISABLED
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth1
       version: 00
       serial: 00:0b:cd:89:e5:8a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:2c00-2cff iomemory:d0009000-d0009fff irq:10
boston@ubuntu:~$ lsmod | grep orinoco
orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
boston@ubuntu:~$ lsmod | grep hostap
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap
boston@ubuntu:~$ lsmod | grep prism2
boston@ubuntu:~$ 

```

What is the system trying to tell us master?

I'm sorry but I thought the " | " after the lsmod command was an "I" earlyer ;-)

---

### Post by chili555 on 2007-05-18
I am a bit mystified by:```
*-network:0 **DISABLED**
```Any idea how that could be? It's not simply because it's not connected, I don't think, because my ethernet is not connected to anything now and does not show as DISABLED.

 Let's also try blacklisting *hostap_pci* Please post back.

---

### Post by helgi on 2007-05-19
> boston@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


boston@ubuntu:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 01
       serial: 00:02:8a:9f:d5:4e
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d000b000-d000bfff irq:10
  *-network:1 DISABLED
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth1
       version: 00
       serial: 00:0b:cd:89:e5:8a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:2c00-2cff iomemory:d0009000-d0009fff irq:10


Network still disabled.

It's like I can't enable the connection from the "Network" window. Whe I click properties and "enable" and exit it doesn't stay enabled. 

I don't know Chili. I was hoping my transition from Windows to linux would be easy. I'm ready to hang in there a little longer though and give it a change....

---

### Post by chili555 on 2007-05-20
Your transition will go very nicely, once we clear this little hurdle. Hang in there; your Prism 2.5 is well supported and will work well. I have one in my older laptop and it's bullet-proof! 

I wonder if the wireless switch has been nudged to 'off.' Open up a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you push the wireless switch. When the switch is off, you might see something like:> Kill switch must be turned off for wireless networking to work.When I switch mine back on, I get:> ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)See if the switch is the problem. Post back so we know how you're getting along.

---

### Post by helgi on 2007-05-20
When you say the "switch" I'm assuming you are talking about that little button on my laptop that turns the wireless card on/off. I entered the code into terminal and pushed the button. Nothing happened. I entered the code again to see if the output would change, which it had not.

```
boston@ubuntu:~$ sudo tail -f /var/log/messages
Password:
May 20 12:22:50 ubuntu hpiod: 1.7.3 accepting connections at 2208... 
May 20 12:22:50 ubuntu kernel: [   39.992000] [drm] Setting GART location based on new memory map
May 20 12:22:50 ubuntu kernel: [   39.992000] [drm] writeback test succeeded in 1 usecs
May 20 12:22:51 ubuntu kernel: [   41.048000] apm: BIOS not found.
May 20 12:23:21 ubuntu gconfd (boston-4817): starting (version 2.18.0.1), pid 4817 user 'boston'
May 20 12:23:21 ubuntu gconfd (boston-4817): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 20 12:23:21 ubuntu gconfd (boston-4817): Resolved address "xml:readwrite:/home/boston/.gconf" to a writable configuration source at position 1
May 20 12:23:21 ubuntu gconfd (boston-4817): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 20 12:23:21 ubuntu gconfd (boston-4817): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 20 12:23:21 ubuntu gconfd (boston-4817): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
```

Any idea what our next step could be?

---

### Post by chili555 on 2007-05-20
Not very many. May we please see the output of```
cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Thanks.

---

### Post by helgi on 2007-05-20
```
boston@ubuntu:~$ cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
cat: /sys/bus/pci/drivers/ipw3945/*/rf_kill: No such file or directory
```

---

### Post by chili555 on 2007-05-20
Shame on ole Chili! Wrong driver. If you drill down in */sys/bus/pci/drivers/* you should find a file rf_kill that contains a single digit. Please try to see what it is.

Sorry for the oops.

---

### Post by helgi on 2007-05-20
No problem Chili.

Wll these are the files in the drivers directory:

```
boston@ubuntu:/sys/bus/pci/drivers$ dir
agpgart-ati    ALI\ 5451    ohci1394     pcieport-driver  uhci_hcd
ali1535_smbus  ata_generic  orinoco_pci  PCI_IDE          yenta_cardbus
ALI15x3_IDE    ehci_hcd     parport_pc   serial
ali15x3_smbus  natsemi      pci_eisa     shpchp

```

Thank you

---

### Post by helgi on 2007-05-20
Hey I picked up a couple of commands from another thread. So as it seems we(you) are running out of ideas. Thus I post them, perhaps they make some revelation...

```
boston@ubuntu:~$ **sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:02:8a:9f:d5:4e
Sending on   LPF/eth0/00:02:8a:9f:d5:4e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
boston@ubuntu:~$ 
```


```
boston@ubuntu:~$ **sudo iwlist eth0 scan**
eth0      Scan completed :
          Cell 01 - Address: 00:18:39:6B:2F:8D
                    ESSID:"Oznet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:8/153  Noise level:7/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:12:17:A9:E9:4A
                    ESSID:"TMAWAP"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:7/153  Noise level:7/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
```

C'mon old Chili, does this tell you anything? I f anybody else sees the solution to the problem please feel more than welcome to comment.

Thanx

---

### Post by helgi on 2007-05-20
Well I desperately want to get to the bottom of this.  I went to my university library and plugged an ethernet cable into my laptop. That worked fine. It was a real pleasure to see some web content for the first time on my Mozilla :) 

I think I'm actually falling in love with Xubuntu. Well at least it's a lot smoother and faster then my ex-OS.
My ex never did what I wanted to do and it was to slow. Also there was the nag all the time.:D

Anyway I don't know how but my network doesn't show disabled anymore:

```
boston@ubuntu:~$ sudo lshw -C network
  ***-network:0             **
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 01
       serial: 00:02:8a:9f:d5:4e
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d000b000-d000bfff irq:10
**  *-network:1**
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth1
       version: 00
       serial: 00:0b:cd:89:e5:8a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half ip=10.16.10.100 latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:2c00-2cff iomemory:d0009000-d0009fff irq:10
```

But still no signal or connection or anything ike that.

Any thoughts?

---

### Post by helgi on 2007-05-20
Well, ole Chili.  I don't know how or why, but I am online right now on a wireless network. So yes everything is working. I really don't know what to say, its a mystery....

But thanks a lot for your help I couldn't have done it without you. Your help was much appreciated!!

:popcorn:

---

### Post by helgi on 2007-05-21
I have discovered that Im able to connect to the wireless connection after i type this command:
```
sudo dhclient eht0
```

I don't know if that is something I should have known or not....

---

### Post by uglydba on 2007-05-30
Hi Guys,

Was just having similar problems with my HP ze5400...same exact card. That blacklist command Chili posted earlier did the trick.

Best Regards,
Brian

---

### Post by Paris Heng on 2007-07-24
Hi,

Do anybody there know how to install Hostapd ?

Please assist.

---

### Post by chili555 on 2007-07-24
sudo apt-get install hostapd

You may also need hostap-utils. You can do this, as well, in Synaptic.

---

### Post by rhydz on 2007-11-25
i am having the same problems cant get it to work. any help would be appreciated

---

