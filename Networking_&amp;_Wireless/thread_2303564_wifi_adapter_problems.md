---
title: "wifi adapter problems"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by Hodor on 2015-11-19
[COLOR=#000000]I have two wifi adapters connected, neither works very well. I'm running ubuntu 14.04.xx 64 on a custom pc (asrock z97 extreme 6, Intel Core i7-4790K ).[/COLOR]

[COLOR=#000000]1. I have an Intel Dual Band Wireless AC 7260 Mini PCI-E Adaptor OEM - this is functioning, but I only get very poor connections (I think the antennae I've connected are inadequate);[/COLOR]

[COLOR=#000000]2. I have a Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter - which the os doesn't seem to be using to connect. It lists under lsusb (Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter), but I'm sure if it was being used to connect me to the router I'd have a better connection that 1 Mb/s (iwconfig)[/COLOR]
[COLOR=#000000]eth0 no wireless extensions.[/COLOR]


[COLOR=#000000]wlan0 IEEE 802.11abgn ESSID:"...' [/COLOR]
[COLOR=#000000]Mode:Managed Frequency:2.462 GHz Access Point: ... [/COLOR]
[COLOR=#000000]Bit Rate=1 Mb/s Tx-Power=22 dBm [/COLOR]
[COLOR=#000000]Retry short limit:7 RTS thr[/COLOR]:eek:[COLOR=#000000]ff Fragment thr[/COLOR]:eek:[COLOR=#000000]ff[/COLOR]
[COLOR=#000000]Power Management[/COLOR]:eek:[COLOR=#000000]n[/COLOR]
[COLOR=#000000]Link Quality=43/70 Signal level=-67 dBm [/COLOR]
[COLOR=#000000]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/COLOR]
[COLOR=#000000]Tx excessive retries:0 Invalid misc:11 Missed beacon:0[/COLOR]


[COLOR=#000000]eth1 no wireless extensions.[/COLOR]


[COLOR=#000000]virbr0 no wireless extensions.[/COLOR]


[COLOR=#000000]lo no wireless extensions.[/COLOR]

[COLOR=#000000]When I look under software, additional drivers: nothing shows up.[/COLOR]

[COLOR=#000000]any advice?[/COLOR]
[COLOR=#000000]- if there's some tips that will get the intel adapter working better, that would be great. A better driver?[/COLOR]
[COLOR=#000000]- otherwise, how do I get the realteck adapter working? Do I need to manually install a driver?[/COLOR]
[COLOR=#000000]- should I remove the intel adapter?

Seems similar to this thread: [/COLOR]http://ubuntuforums.org/showthread.php?t=2194689
I'll look on the realtek site for drivers.

---

### Post by slickymaster on 2015-11-19
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums

---

### Post by Hodor on 2015-11-19
Thanks slickymaster. see info below.

---

### Post by Bucky Ball on 2015-11-19
> **Hodor said:**
> I have two wifi adapters connected ...

At the same time??? If so, unplug one and work on one or the other, not both, and have the cable unplugged unless you need to download stuff to get wireless working. 

I suggest you unplug everything, switch the machine off, plug in one wifi dongle, boot, run:

```
sudo lshw -C network
```

... or the wireless script (see link in my signature), as suggested, and post the result here between code tags (last link in my signature).

---

### Post by Hodor on 2015-11-19
Here's the output for 'sudo lshw -C network'only the realteck wifi dongle plugged in,  (with some serial numbers anonymised '...' - let me know if you need the full id):
[COLOR=#000000]```
 [/COLOR]*-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 00
       serial: d0:50:99:...
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:56 memory:eff00000-eff1ffff memory:eff3c000-eff3cfff ioport:f080(size=32)
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: d0:50:99:...
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:57 ioport:e000(size=256) memory:efd00000-efd00fff memory:e0000000-e0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:2
       logical name: wlan1
       serial: e8:4e:06:...
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
[COLOR=#000000]
```[/COLOR]
=================================================================================
Some background:
- On windows I can turn off individual adaptors through the os (handy, since the intel wireless adapter is a mini-pcie express card that was screwed in under my sm951 M.2, not an easy 'unplug'). Is there no way to do this in Ubuntu?
- I'd left the intel mini-pcie in, since if I can't get the realtek to work I'll need to get out my screwdriver again and see if I then can get the intel to work (maybe buy a better antenna).
- my plan is to mostly work off the ethernet adapter, and would normally only have one on at a time (I disable the wireless networking when I don't need it). But the ethernet connects to a router that's bridged (WDS) to the main router, so the speed is slower than I can get with a decent wifi adapter (so I'll sometimes want to use the latter if I can get one to work).

---

### Post by Bucky Ball on 2015-11-19
> **Bucky Ball said:**
> ... post the result here between code tags (last link in my signature).

You missed this? Sorry, but need to go out for a few hours. Will catch up on it later and in the meantime hopefully someone else leaps in.

---

### Post by Hodor on 2015-11-19
Sorry, now fixed.

---

### Post by slickymaster on 2015-11-20
Glad to know you got it fixed.

Please share with the forums the process you used to manage to solve your issue and mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Bucky Ball on 2015-11-20
> **slickymaster said:**
> glad to know you got it fixed.

Please share with the forums the process you used to manage to solve your issue and mark the thread as [solved]("https://wiki.ubuntu.com/unansweredpoststeam/solvedthreads").

+1. :)

---

### Post by Hodor on 2015-11-20
By fixed I meant '[COLOR=#000000][I]... post the result here between code tags (last link in my signature).' is now fixed - I still have a problem with my wifi.
I tried downloading the driver from [[/I][/COLOR]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true[COLOR=#000000][I]] and ran the install script but I got a make error 
(There's a lot of warnings like ''[/I][/COLOR]warning: cast from pointer to integer of different size ...'  then 'some warnings being treated as errors'.[COLOR=#000000][I])
 I wonder if the problem is the kernel version (the driver requires [/I][/COLOR][COLOR=#666666][FONT=Arial]Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2, my kernel is [/FONT][/COLOR]3.16.0-53-generic[COLOR=#000000][I]).

[/I][/COLOR]

---

### Post by Hodor on 2015-11-20
The realtek runs out of the box on an x86 version of ubuntu 12.02 (kernel 3.13.0-63-generic.)

---

### Post by praseodym on 2015-11-20
Try these module parameters for the stick and the ones for the internal card:
```

echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
```
Reboot and check
```

sudo iwconfig wlan0 power off
```
Now check both the internal card and the stick

---

### Post by Hodor on 2015-11-20
Thanks praseodym! my realtek adapter now works, so I've marked the tread solved.  I haven't re-installed the intel card yet so I can't comment on how that's functioning - I'll post an update when the card's back in and I've looked at it.

---

### Post by Hodor on 2015-11-21
Hi praseodym, I've reconnected the internal card - the connection has improved but only to 11 Mb/s.  Any suggestions?  This card and my router should connect at 5 GHz / ac.  Is there a link to where I can learn more about this wifi mx on ubuntu / linux ? 
Updating the windows driver produced a major improvement.
Looking at the Linux drivers ([http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)), it appears I need a 4.1 or 4.2 kernel to update these.  I'm not keen on 15.10 so I might have to wait for 16.04 to use the Intel card on Ubuntu.
Any advice much appreciated.
 Thanks very much.

---

### Post by praseodym on 2015-11-22
Lets check:
```

lspci -nnk | grep -iA2 net
dmesg | egrep 'firm|wlan|iwl'
```

---

### Post by Hodor on 2015-11-22
Result from the above:
```

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	Subsystem: ASRock Incorporation Device [1849:15a1]
	Kernel driver in use: e1000e
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi

```

---

### Post by Hadaka on 2015-11-22
Hi, please post the output of..
```
modinfo iwlwifi | grep -i "8086:08B1"
modinfo iwlwifi | grep -i "8086:4070"
```
*If you get no output then you can try...
[URL="http://ubuntuforums.org/showthread.php?t=2242147&page=2"]http://ubuntuforums.org/showthread.php?t=2242147&page=2
[/URL]post #12 or 19
or
wait for praseodym who may have a one click file.
good luck.

---

### Post by praseodym on 2015-11-22
The "dmesg" output is missing

---

### Post by Hodor on 2015-11-22
Sorry, herewith (I have the realtek usb removed while working on the Intel card and I've anonymised some mac type data, '...', let me know if you need full data for any of this):
```

user-desktop:~$ dmesg | egrep 'firm|wlan|iwl'
[    2.724869] iwlwifi 0000:07:00.0: enabling device (0000 -> 0002)
[    2.724985] iwlwifi 0000:07:00.0: irq 60 for MSI/MSI-X
[    2.738867] iwlwifi 0000:07:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.793464] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.793516] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.793751] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.002491] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.320106] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.320341] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.332224] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.608998] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[    4.657743] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    6.948323] wlan0: authenticate with 30:85:a9:...
[    6.950215] wlan0: send auth to 30:85:a9:... (try 1/3)
[    6.950858] wlan0: authenticated
[    6.951902] wlan0: associate with 30:85:a9:... (try 1/3)
[    6.952946] wlan0: RX AssocResp from 30:85:a9:... (capab=0x11 status=0 aid=2)
[    6.953831] wlan0: associated
[    6.953851] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.274647] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c0:... SRC=192.168.1.2 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[    7.887816] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c0:... SRC=192.168.1.2 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   23.549785] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c0:... SRC=192.168.1.2 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

```

---

### Post by Hodor on 2015-11-22
Thanks Hadaka,
I don't get any output for either command.
I'm looking through post #12 and 19.
I'm on a production system which I'd like to be stable so I think 19 is not the way to go.
Looking at 12 - am I correct in thinking that if this doesn't work I will have just compiled a driver that doesn't work; my system, apart from the intel card, is undamaged?  
In that case, compiling my own driver sounds like fun.
But if the stability of my os more generally might be undermined by the driver not working I'd rather play with that on a different system or just wait for 16.04.
Also, if #12 looks fine in those terms, how do I confirm that my device is the exact same as this post ('[COLOR=#000000]CAUTION to searchers: Unless your device is the exact same, Intel Corporation Wireless 7260 [8086:08b1] (rev cb)')?
[/COLOR]The Intel Wireless 7260 comes in several form factors, mine is the mini-pcie, 7260HMW (see [http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth-brief.html](http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth-brief.html))
Any advice on this?

---

### Post by Hadaka on 2015-11-22
Hi,probably if you made sure you had zero typo's and it still failed
it should not have any effect on anything else. Key word be being "should"
Your first post says you can connect to the 7260  intel but its weak. I am
surprised you connect at all if you are not showing any output on those modinfo commands,
You would be wise at this point,since you are functional to wait on the advise of praseodym.
He has alot more knowledge than I, and as I stated earlier,probably a known working file, so be
patient and im sure praseodym will help you find a solution.

---

### Post by Hodor on 2015-11-22
Thanks Hadaka, I'll wait for praseodym.
No output, like below, with the card connecting to the router/internet:
user-desktop:~$ modinfo iwlwifi | grep -i "8086:08B1"
user-desktop:~$ modinfo iwlwifi | grep -i "8086:4070"
user-desktop:~$

---

### Post by praseodym on 2015-11-24
Uninstall the firewall:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by Hodor on 2015-11-24
Awesome praseodym, you're a legend (joy is me):
```

user@user-desktop:~/$ iwconfig
eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"myrouter"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: ...   
          Bit Rate=195.1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:29   Missed beacon:0

```

Thank you

---

### Post by praseodym on 2015-11-25
You're welcome. If wifi is too slow deactivate the power management:
```

sudo iwconfig wlan0 power off
iwconfig
```

---

