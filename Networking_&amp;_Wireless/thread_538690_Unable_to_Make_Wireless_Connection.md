---
title: "Unable to Make Wireless Connection"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Trevor4706 on 2007-08-30
I am running Kubuntu Feisty on my laptop.  It recognized my GigaFast WF728-AEX PCMIA wireless adapter out of the box and I had no difficulty using it to connect to wireless networks when I was on the road several months ago.  Since then I have updated my installation several times.  My home LAN is wired, so I have not tried any wireless connections until another road trip last week.  I was unable to make any connections, either open or secured.  KNetworkManager hung at the 28% mark and then timed out.  Back to dial-up for the duration of my trip.

My ISP just upgraded my service and sent me a new DSL modem with a built-in wireless option. I can connect the laptop to my LAN via a wired connection but, even though the new WEP-protected wireless LAN was detected, I still could not connect to it by wireless.  After reading many of the posts in this forum I uninstalled KNetworkManager and installed wicd.  Wicd detected the network with no difficulty, but I still cannot connect.  Wicd hangs during the connection process and times out.  It seems to me that both KNetworkManager and wicd cannot obtain an IP address.  Over the past few days I've tried most of the work-arounds I have found in this forum without success, and am beginning to think I may be compounding things.

Any fresh insight would be appreciated.

---

### Post by noob12 on 2007-08-30
How about posting the output of these when in the vicinity of your new wireless router/modem?

```

sudo lshw -C network

sudo iwlist scan

iwconfig

```

---

### Post by Trevor4706 on 2007-08-30
noob12

Here goes:

sudo lshw -C network

*-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:98:c6:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half ip=192.168.0.100 latency=32 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:e0100000-e0101fff irq:10
 *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: wmaster0
       version: 01

sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz
          RTS thr: off   Fragment thr=2346 B

eth1      IEEE 802.11g  ESSID:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr: off   Fragment thr=2346 B
          Encryption key: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
       serial: 00:0a:e9:08:67:2d
       width: 32 bits

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

eth1      Scan completed :
          Cell 01 - Address: 00:1B:5B:6F:AC:11
                    ESSID:"BELL951"
                    Mode:Master
                    Frequency:2.427 GHz
                    Signal level=68/100
                    Encryption key: on
                    Extra:tsf=000000160fbf7181

       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:48000000-48001fff irq:10

---

### Post by ZShakespeare on 2007-08-30
I've been having a very similar problem. The only way I've been able to get it to work is by booting from my Ubuntu, or PCLinuxOS2007 LiveCD, using that to connect to the wireless, and then rebooting back into kubuntu. Everything works fine after that. The problem seems to occur at least once a day for me.

---

### Post by ubunteduser on 2007-08-30
I have a problem with similar symptoms but with Ubuntu.But I found a work around.

My solution is try to connect to a new wirless network that doesn't exist and the after 10 seconds click to connect to the network that does. 

> **Trevor4706 said:**
> I I was unable to make any connections, either open or secured.  KNetworkManager hung at the 28% mark and then timed out.  Back to dial-up for the duration of my trip.

---

### Post by noob12 on 2007-08-31
trevor4706:   To get started, I would disable the encryption on your local access point, enable ESSID broadcast on the access point, and try connecting first that way, then reintroduce encryption to the picture.  

See if you can get to an associated state which would be shown in **iwconfig** output even if you don't get an IP address.

---

### Post by Trevor4706 on 2007-08-31
noob12

I'm "on the road again", back in the land of dial-up access, and will have to wait until I return home next week to give your suggestion a try.  Just exactly what does "associated state" mean?  Somewhere between have an IP address and no contact whatsoever?

---

### Post by noob12 on 2007-08-31
It means that the wireless card has associated successfully with the access point, and any WEP/WPA authentication has completed.  It is somewhat analogous to achieving a wired link.  This is a prerequisite to getting any IP packets across.   After that your machine will typically be doing DHCP to get an address, etc.

---

### Post by Trevor4706 on 2007-09-08
noob12

I'm getting somewhere.  When I got home today I tried once again to connect with the wireless router.  It looks like I've achieved connection at last.  Please see the results of iwconfig after the connection was achieved.  The "xxx-xxxx ..." is my correct 26 hex character WEP key.  Problem is, I cannot connect with the internet.  Firefox and Thunderbird both time-out.  I ran ifconfig and eth1 (my wireless card) is showing an IP address of 192.168.2.10, which looks like a valid ip address.

sudo iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 IEEE 802.11g Frequency:2.412 GHz
RTS thr: off Fragment thr=2346 B

eth1 IEEE 802.11g ESSID:"BELL915"
Mode:Managed Frequency:2.412 GHz Access Point: 00:1B:5B:6F:AC:11
RTS thr: off Fragment thr=2346 B
Encryption key: xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx
Link Signal level:+58/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I think I must be missing something basic here.  Any suggestions?

Trevor4706:confused:

---

### Post by kevdog on 2007-09-08
Try the following

sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "BELL915"
sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 key HEXKEYHEREWITHOUTDASHESORSPACES
sudo dhclient eth1

---

